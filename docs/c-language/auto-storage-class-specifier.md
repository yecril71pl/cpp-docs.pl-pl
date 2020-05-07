---
title: Specyfikator automatycznej klasy magazynowania
ms.date: 11/04/2016
ms.assetid: 8e73f57e-aa92-4e41-91ea-5c8ad2a2b332
ms.openlocfilehash: 6bd36fd534602a5a4df95047a830058e8c5ef163
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62313470"
---
# <a name="auto-storage-class-specifier"></a>Specyfikator automatycznej klasy magazynowania

Specyfikator klasy magazynu **automatycznego** deklaruje zmienną automatyczną, zmienną z lokalnym okresem istnienia. Zmienna **auto** autovariable jest widoczna tylko w bloku, w którym jest zadeklarowana. Deklaracje **autozmiennych mogą** zawierać inicjatory, zgodnie z opisem w [inicjalizacji](../c-language/initialization.md). Ze względu na to, że zmienne z klasą **automatycznego** magazynu nie są inicjowane automatycznie, należy je jawnie zainicjować przy deklarowaniu ich lub przypisać do nich wartości początkowe w instrukcjach w bloku. Wartości niezainicjowanych **zmiennych** autonie są zdefiniowane. (Lokalna zmienna klasy magazynu autolub **register** jest inicjowana za każdym **razem, gdy** występuje inicjator.)

Wewnętrzna zmienna **statyczna** (zmienna statyczna z zakresem lokalnym lub blokowym) może zostać zainicjowana przy użyciu adresu dowolnego elementu zewnętrznego lub **statycznego** , ale nie z **adresem innego elementu** **autoitem, ponieważ adres elementu** autoitem nie jest stałą.

## <a name="see-also"></a>Zobacz też

[Słowo kluczowe "Autouzupełnianie"](../cpp/auto-keyword.md)
