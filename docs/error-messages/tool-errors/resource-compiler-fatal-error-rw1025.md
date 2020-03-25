---
title: Błąd krytyczny kompilatora zasobów RW1025
ms.date: 11/04/2016
f1_keywords:
- RW1025
helpviewer_keywords:
- RW1025
ms.assetid: 561a02af-e7e0-442a-8ad3-a00b2ca1b62e
ms.openlocfilehash: 9b6697dff0a445cc342f30d08bd79822b02df7b8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80172728"
---
# <a name="resource-compiler-fatal-error-rw1025"></a>Błąd krytyczny kompilatora zasobów RW1025

Za mało pamięci sterty

Sprawdź, czy jest używane oprogramowanie rezydentne pamięci, które może zużywać zbyt dużo miejsca. Użyj programu CHKDSK, aby dowiedzieć się, ile masz pamięci.

W przypadku tworzenia dużego pliku zasobów Podziel skrypt zasobu na dwa pliki. Po utworzeniu dwóch plików. res Użyj wiersza polecenia systemu MS-DOS, aby dołączyć je razem:

```
copy first.res /b + second.res /b full.res
```
