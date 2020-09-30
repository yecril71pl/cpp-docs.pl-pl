---
title: Błąd kompilatora C3345
ms.date: 11/04/2016
f1_keywords:
- C3345
helpviewer_keywords:
- C3345
ms.assetid: 1dda4c79-73bb-441b-b939-746154c3afba
ms.openlocfilehash: 8682069fdf719f4e85d1d6f5107de1903e3ae071
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91504845"
---
# <a name="compiler-error-c3345"></a>Błąd kompilatora C3345

"Identyfikator": nieprawidłowy identyfikator dla nazwy modułu

*Identyfikator* modułu zawiera jeden lub więcej nieakceptowalnych znaków. Identyfikator jest prawidłowy, jeśli pierwszy znak jest znakiem alfabetycznym, podkreśleniem lub High ANSI (0x80-FF), a każdy kolejny znak jest znakiem alfanumerycznym, podkreśleniem lub dużą ANSI.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

1. Upewnij się, że *Identyfikator* nie zawiera pustych lub innych nieakceptowalnych znaków.

## <a name="example"></a>Przykład

Poniższy przykład kodu powoduje, że komunikat o błędzie C3345, ponieważ `name` parametr `module` atrybutu zawiera pustą wartość.

```cpp
// cpp_attr_name_module.cpp
// compile with: /LD /link /OPT:NOREF
#include <atlbase.h>
#include <atlcom.h>
#include <atlwin.h>
#include <atltypes.h>
#include <atlctl.h>
#include <atlhost.h>
#include <atlplus.h>

// C3345 expected
[module(dll, name="My Library", version="1.2", helpfile="MyHelpFile")]
// Try the following line instead
//[module(dll, name="MyLibrary", version="1.2", helpfile="MyHelpFile")]
// Module attribute now applies to this class
class CMyClass {
public:
BOOL WINAPI DllMain(DWORD dwReason, LPVOID lpReserved) {
   // add your own code here
   return __super::DllMain(dwReason, lpReserved);
   }
};
```

## <a name="see-also"></a>Zobacz też

[__iscsym](../../c-runtime-library/reference/iscsym-functions.md)<br/>
[Klasyfikacja znaków](../../c-runtime-library/character-classification.md)<br/>
[elementu](../../windows/attributes/module-cpp.md)
