---
tags:
  - debugging
---

## Base set of breakpoints
- `_uassertfunc` in `main.c`
- `DefaultHandler` in `VectorTable.c`

## Watch display
### GDB (target)
#### See value in hex
  `value,x`
  Right-click and choose "hex view"
#### Arrays
  Click tiny icon at the right of the entry in the locals or watch window and it will open a memory window
  `(uint8_t *[40])instance->_private.receiveBuffer`
### LLDB (TDD)
  `-exec type format add --format Y uint8_t` will format all `char` variables to display both hex and ASCII

  See https://lldb.llvm.org/use/variable.html#type-format

## TDD
### Dump stack
Unfortunately, this gives functions, but not line numbers.
```
   char *GetBacktraceSymbols()
   {
      static const int backtraceDepth = 20;
      void *backtraceArray[backtraceDepth];
      int numberOfElementsFilled = backtrace(backtraceArray, backtraceDepth);
      char **symbolsArray = backtrace_symbols(backtraceArray, numberOfElementsFilled);
      size_t totalLength = strlen("At:\n");
      int numberOfElementsToPrint;
      for(numberOfElementsToPrint = 1; numberOfElementsToPrint < numberOfElementsFilled; numberOfElementsToPrint++)
      {
         if(strstr(symbolsArray[numberOfElementsToPrint], "helperDoTestBody") != NULL)
         {
            break;
         }
         totalLength += strlen(symbolsArray[numberOfElementsToPrint]) + strlen("\n");
      }

      char *combinedString = (char *)calloc(totalLength + 1, 1);
      strcat(combinedString, "At:\n");
      for(int i = 1; i < numberOfElementsToPrint; i++)
      {
         strcat(combinedString, symbolsArray[i]);
         strcat(combinedString, "\n");
      }
      free(symbolsArray);
      return combinedString;
   }

#define BYTES_EQUAL_WITH_BACKTRACE(expected, actual)        \
   {                                                        \
      char *backtraceSymbols = GetBacktraceSymbols();       \
      BYTES_EQUAL_TEXT(expected, actual, backtraceSymbols); \
      free(backtraceSymbols);                               \
   }
```
