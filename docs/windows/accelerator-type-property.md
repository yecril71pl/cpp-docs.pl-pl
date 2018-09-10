---
title: Właściwość typu akceleratora (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Type property
- VIRTKEY
ms.assetid: 8c349bc4-e6ad-43fa-959e-f29168af35b8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d38d5a78eb37a028f29da430a762604b2e50d632
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44315694"
---
# <a name="accelerator-type-property-c"></a>Właściwość typu akceleratora (C++)

Akcelerator **typu** właściwość określa, czy klawisz skrótu skojarzony identyfikator akceleratora jest wirtualny kombinacji klawiszy lub ASCII/ANSI wartość klucza:

- Jeśli **typu** właściwość jest ASCII, [modyfikator](../windows/accelerator-modifier-property.md) może składać się wyłącznie `None` lub `Alt`, lub może być akceleratora, który używa **Ctrl** (określony przez klucz klucza z poprzednich `^`).

- Jeśli **typu** właściwość jest VIRTKEY i dowolną kombinację `Modifier` i `Key` wartości jest prawidłowy.

   > [!NOTE]
   > Jeśli chcesz wprowadzić wartość w tabeli akceleratora i wartości traktowane jak ASCII/ANSI, po prostu kliknij **typu** wpisu w tabeli i ASCII wybierz z listy rozwijanej. Jednak jeśli używasz **dalej wpisany klucz** polecenia (**Edytuj** menu) do określenia `Key`, należy zmienić **typu** właściwość VIRTKEY ASCII *przed* wprowadzania `Key` kodu.

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Ustawianie właściwości klawiszy skrótów](../windows/setting-accelerator-properties.md)  
[Edytor klawiszy skrótów](../windows/accelerator-editor.md)