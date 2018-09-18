---
title: Błąd kompilatora C3345 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3345
dev_langs:
- C++
helpviewer_keywords:
- C3345
ms.assetid: 1dda4c79-73bb-441b-b939-746154c3afba
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 191c2184d14f991ab62f439b492c7fd7f4a00be5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118950"
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

## <a name="see-also"></a>Zobacz też

[__iscsym](../../c-runtime-library/reference/iscsym-functions.md)<br/>
[Klasyfikacja znaków](../../c-runtime-library/character-classification.md)<br/>
[Moduł](../../windows/module-cpp.md)