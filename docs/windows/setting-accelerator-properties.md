---
title: Ustawianie właściwości klawiszy skrótów (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- accelerator properties
- properties [C++], accelerator properties
- Type property
- Key property
- Modifier property
ms.assetid: 0fce9156-3025-4e18-b034-e219a4c65812
ms.openlocfilehash: 47ebd54fdaff099e3a8ce828581a66b0ec871915
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50647021"
---
# <a name="setting-accelerator-properties"></a>Ustawianie właściwości klawiszy skrótów

Można ustawić właściwości klawiszy skrótów w [okno właściwości](/visualstudio/ide/reference/properties-window) w dowolnym momencie. Można również użyć **akceleratora** edytora, aby zmodyfikować właściwości klawiszy skrótów w tabeli klawiszy skrótu. Zmiany wprowadzone przy użyciu **właściwości** okna lub **akceleratora** Edytor ma ten sam wynik: zmiany są natychmiast odzwierciedlane w tabeli klawiszy skrótu.

Istnieją trzy właściwości dla każdego identyfikator akceleratora:

- [Właściwość modyfikatora](../windows/accelerator-modifier-property.md) formant kombinacje klawiszy dla akceleratora.

   > [!NOTE]
   > W **właściwości** , ta właściwość zostanie wyświetlone okno jako trzy osobne właściwości logiczne, które mogą być kontrolowane niezależnie: **Alt**, **Ctrl**i **Shift**.

- [Właściwości klucza](../windows/accelerator-key-property.md) ustawia rzeczywistego klucza do użycia jako akcelerator.

- [Właściwość typu](../windows/accelerator-type-property.md) Określa, czy klucz jest interpretowane jako wirtualny (VIRTKEY) lub ASCII/ANSI.

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Wstępnie zdefiniowane klawisze skrótów](../windows/predefined-accelerator-keys.md)<br/>
[Edytory zasobów](../windows/resource-editors.md)<br/>
[Edytor klawiszy skrótów](../windows/accelerator-editor.md)