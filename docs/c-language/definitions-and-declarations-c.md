---
title: Definicje i deklaracje (C)
ms.date: 11/04/2016
helpviewer_keywords:
- export functions
ms.assetid: d150395a-89d4-4298-9ac4-08f84fe1261c
ms.openlocfilehash: 0e39832f942eb1473be913112fde1d37ddf05674
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226369"
---
# <a name="definitions-and-declarations-c"></a>Definicje i deklaracje (C)

**Specyficzne dla firmy Microsoft**

Interfejs DLL odwołuje się do wszystkich elementów (funkcji i danych), które są znane do wyeksportowania przez jakiś program w systemie. oznacza to, że wszystkie elementy, które są zadeklarowane jako **`dllimport`** lub `dllexport` . Wszystkie deklaracje zawarte w interfejsie DLL muszą określać **`dllimport`** `dllexport` atrybut lub. Jednak definicja może określać tylko `dllexport` atrybut. Na przykład następująca definicja funkcji generuje błąd kompilatora:

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

Użycie `dllexport` wskazuje definicję, a mimo to **`dllimport`** oznacza deklarację. Musisz użyć **`extern`** słowa kluczowego with, `dllexport` Aby wymusić deklarację; w przeciwnym razie jest implikowana definicja.

```
#define DllImport   __declspec( dllimport )
#define DllExport   __declspec( dllexport )

extern DllImport int k;   /* These are correct and imply */
Dllimport int j;          /* a declaration. */
```

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje importowania i eksportowania biblioteki DLL](../c-language/dll-import-and-export-functions.md)
