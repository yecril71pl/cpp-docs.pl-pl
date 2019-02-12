---
title: Definicje i deklaracje (C)
ms.date: 11/04/2016
helpviewer_keywords:
- export functions
ms.assetid: d150395a-89d4-4298-9ac4-08f84fe1261c
ms.openlocfilehash: 8723c3f09a5e9a8eecf0e552c9f5a7fd9b7f6c68
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2019
ms.locfileid: "56152368"
---
# <a name="definitions-and-declarations-c"></a>Definicje i deklaracje (C)

**Microsoft Specific**

Interfejsu biblioteki DLL, który odwołuje się do wszystkich elementów (funkcje i dane), które są znane mają zostać wyeksportowane przez program w systemie; oznacza to, że wszystkie elementy, które są zadeklarowane jako **dllimport** lub `dllexport`. Należy określić wszystkie deklaracje objęte interfejsu biblioteki DLL **dllimport** lub `dllexport` atrybutu. Jednak tylko określić definicję `dllexport` atrybutu. Na przykład następująca definicja funkcji generuje błąd kompilatora:

```
#define DllImport   __declspec( dllimport )
#define DllExport   __declspec( dllexport )

DllImport int func()    /* Error; dllimport prohibited in */
                        /* definition. */
{
   return 1;
}
```

Ten kod jest również generuje błąd:

```
#define DllImport   __declspec( dllimport )
#define DllExport   __declspec( dllexport )

DllImport int i = 10;      /* Error; this is a definition. */
```

Jednak jest to prawidłowa składnia:

```
#define DllImport   __declspec( dllimport )
#define DllExport   __declspec( dllexport )

DllExport int i = 10;      /* Okay: this is an export definition. */
```

Korzystanie z `dllexport` oznacza definicję, podczas gdy **dllimport** zakłada deklarację. Należy użyć `extern` — słowo kluczowe z `dllexport` Aby wymusić deklarację; w przeciwnym razie jest implikowane definicję.

```
#define DllImport   __declspec( dllimport )
#define DllExport   __declspec( dllexport )

extern DllImport int k;   /* These are correct and imply */
Dllimport int j;          /* a declaration. */
```

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Importowanie bibliotek DLL i eksportowanie funkcji](../c-language/dll-import-and-export-functions.md)
