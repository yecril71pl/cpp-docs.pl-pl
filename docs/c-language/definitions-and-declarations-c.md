---
title: Definicje i deklaracje (C)
ms.date: 11/04/2016
helpviewer_keywords:
- export functions
ms.assetid: d150395a-89d4-4298-9ac4-08f84fe1261c
ms.openlocfilehash: 8723c3f09a5e9a8eecf0e552c9f5a7fd9b7f6c68
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62234361"
---
# <a name="definitions-and-declarations-c"></a>Definicje i deklaracje (C)

**Specyficzne dla firmy Microsoft**

Interfejs DLL odwołuje się do wszystkich elementów (funkcji i danych), które są znane do wyeksportowania przez jakiś program w systemie. oznacza to, że wszystkie elementy, które są **dllimport** zadeklarowane `dllexport`jako dllimport lub. Wszystkie deklaracje zawarte w interfejsie DLL muszą określać **dllimport** atrybut dllimport `dllexport` lub Attribute. Jednak definicja może określać tylko `dllexport` atrybut. Na przykład następująca definicja funkcji generuje błąd kompilatora:

```
#define DllImport   __declspec( dllimport )
#define DllExport   __declspec( dllexport )

DllImport int func()    /* Error; dllimport prohibited in */
                        /* definition. */
{
   return 1;
}
```

Ten kod również generuje błąd:

```
#define DllImport   __declspec( dllimport )
#define DllExport   __declspec( dllexport )

DllImport int i = 10;      /* Error; this is a definition. */
```

Jest to jednak poprawna składnia:

```
#define DllImport   __declspec( dllimport )
#define DllExport   __declspec( dllexport )

DllExport int i = 10;      /* Okay: this is an export definition. */
```

Użycie `dllexport` wskazuje definicję, podczas gdy **dllimport** oznacza deklarację. Aby wymusić `extern` deklarację, należy użyć słowa kluczowego. `dllexport` w przeciwnym razie jest implikowana definicja.

```
#define DllImport   __declspec( dllimport )
#define DllExport   __declspec( dllexport )

extern DllImport int k;   /* These are correct and imply */
Dllimport int j;          /* a declaration. */
```

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[Importowanie bibliotek DLL i eksportowanie funkcji](../c-language/dll-import-and-export-functions.md)
