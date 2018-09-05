---
title: Ustawianie właściwości klawiszy skrótów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- accelerator properties
- properties [C++], accelerator properties
- Type property
- Key property
- Modifier property
ms.assetid: 0fce9156-3025-4e18-b034-e219a4c65812
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b89f409fcf5a856a2207dd8efa655728f57b3fe8
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43680138"
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

[Wstępnie zdefiniowane klawisze skrótów](../windows/predefined-accelerator-keys.md)  
[Edytory zasobów](../windows/resource-editors.md)  
[Edytor klawiszy skrótów](../windows/accelerator-editor.md)