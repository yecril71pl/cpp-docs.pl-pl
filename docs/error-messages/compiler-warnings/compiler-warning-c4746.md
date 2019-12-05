---
title: Ostrzeżenie kompilatora C4746
ms.date: 11/04/2016
f1_keywords:
- C4746
helpviewer_keywords:
- C4746
ms.assetid: 5e79ab46-6031-499a-a986-716c866b6c0e
ms.openlocfilehash: 9e761deb1b8c1b00e025f49775a845d07985fd2c
ms.sourcegitcommit: 8762a3f9b5476b4dee03f0ee8064ea606550986e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/04/2019
ms.locfileid: "74810568"
---
# <a name="compiler-warning-c4746"></a>Ostrzeżenie kompilatora C4746

nietrwały dostęp elementu "\<expression >" podlega ustawieniu/volatile: [&#124;ISO MS]; Rozważ __iso_volatile_load użycie funkcji wewnętrznych/Store.

C4746 jest emitowany za każdym razem, gdy jest uzyskiwany bezpośredni dostęp do zmiennej lotnej. Ma ona ułatwić deweloperom zidentyfikowanie lokalizacji kodu, na które ma wpływ określony model nietrwały, który jest aktualnie określony (który może być kontrolowany przy użyciu opcji kompilatora [/volatile](../../build/reference/volatile-volatile-keyword-interpretation.md) ). W szczególności może to być przydatne podczas lokalizowania barier pamięci sprzętowej generowanych przez kompilator, gdy jest używany/volatile: MS.

W celu jawnego uzyskiwania dostępu do pamięci lotnej bez wpływu na nietrwały model, można użyć funkcji wewnętrznych __iso_volatile_load/Store. Użycie tych elementów wewnętrznych nie spowoduje wyzwolenia C4746.

To ostrzeżenie jest domyślnie wyłączone. Aby uzyskać więcej informacji [, zobacz ostrzeżenia kompilatora, które są domyślnie wyłączone](../../preprocessor/compiler-warnings-that-are-off-by-default.md) .