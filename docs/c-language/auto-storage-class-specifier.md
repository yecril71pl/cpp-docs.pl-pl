---
title: Specyfikator automatycznej klasy magazynowania
ms.date: 11/04/2016
ms.assetid: 8e73f57e-aa92-4e41-91ea-5c8ad2a2b332
ms.openlocfilehash: e39b37e2dc91dce31b6871d721875c75b8ebd629
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223762"
---
# <a name="auto-storage-class-specifier"></a>`auto`Specyfikator klasy magazynu

**`auto`** Specyfikator klasy magazynowania deklaruje zmienną automatyczną, zmienną z lokalnym okresem istnienia. **`auto`** Zmienna jest widoczna tylko w bloku, w którym jest zadeklarowana. Deklaracje **`auto`** zmiennych mogą zawierać inicjatory, zgodnie z opisem w [inicjalizacji](../c-language/initialization.md). Ze względu na to, że zmienne z **`auto`** klasą magazynu nie są inicjowane automatycznie, należy je jawnie zainicjować przy deklarowaniu ich lub przypisać do nich wartości początkowe w instrukcjach w bloku. Wartości niezainicjowanych **`auto`** zmiennych są niezdefiniowane. (Lokalna zmienna **`auto`** lub **`register`** Klasa magazynu jest inicjowana za każdym razem, gdy występuje, gdy inicjator jest określony).

Zmienna wewnętrzna **`static`** (zmienna statyczna z zakresem lokalnym lub blokowym) może zostać zainicjowana przy użyciu adresu dowolnego **`static`** elementu zewnętrznego lub, ale nie z adresem innego **`auto`** elementu, ponieważ adres **`auto`** elementu nie jest stałą.

## <a name="see-also"></a>Zobacz także

[`auto`Kodu](../cpp/auto-keyword.md)
