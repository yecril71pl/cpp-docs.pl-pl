---
title: Błąd kompilatora C3345
ms.date: 11/04/2016
f1_keywords:
- C3345
helpviewer_keywords:
- C3345
ms.assetid: 1dda4c79-73bb-441b-b939-746154c3afba
ms.openlocfilehash: eb1d15a12bfebbf44f7335a848d68c367c285586
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59027562"
---
# <a name="compiler-error-c3345"></a>Błąd kompilatora C3345

'Identyfikator': nieprawidłowy identyfikator dla nazwy modułu

*Identyfikator* moduł zawiera jeden lub więcej znaków nie do przyjęcia. Identyfikator jest prawidłowy, jeśli pierwszy znak jest znakiem alfabetycznym, podkreślenia, lub wysokie ANSI (0x80 FF), wszystkie kolejne znaków i litery, cyfry, podkreślenia ani znaków ANSI wysoka.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

1. Upewnij się, że *identyfikator* nie zawiera spacje lub znaki nie do przyjęcia.

## <a name="example"></a>Przykład

Poniższy przykładowy kod powoduje komunikat o błędzie C3345, ponieważ `name` parametru `module` atrybut zawiera puste.

```
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

## <a name="see-also"></a>Zobacz także

[__iscsym](../../c-runtime-library/reference/iscsym-functions.md)<br/>
[Klasyfikacja znaków](../../c-runtime-library/character-classification.md)<br/>
[module](../../windows/module-cpp.md)