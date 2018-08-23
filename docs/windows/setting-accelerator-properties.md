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
ms.openlocfilehash: 5d47dffb782da1094c157a7bbd21c40ab6ba9fef
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42606707"
---
# <a name="setting-accelerator-properties"></a>Ustawianie właściwości klawiszy skrótów

Można ustawić właściwości klawiszy skrótów w [okno właściwości](/visualstudio/ide/reference/properties-window) w dowolnym momencie. Można również użyć **akceleratora** edytora, aby zmodyfikować właściwości klawiszy skrótów w tabeli klawiszy skrótu. Zmiany wprowadzone przy użyciu **właściwości** okna lub **akceleratora** Edytor ma ten sam wynik: zmiany są natychmiast odzwierciedlane w tabeli klawiszy skrótu.

Istnieją trzy właściwości dla każdego akceleratora [identyfikator](https://www.microsoftonedoc.com/#/organizations/e6f6a65cf14f462597b64ac058dbe1d0/projects/3fedad16-eaf1-41a6-8f96-0c1949c68f32/containers/a3daf831-1c5f-4bbe-964d-503870caf874/tocpaths/3487f185-de96-4b1d-87db-034a52223160):

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