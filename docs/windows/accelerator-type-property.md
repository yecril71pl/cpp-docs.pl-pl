---
title: Właściwość typu akceleratora (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- Type property
- VIRTKEY
ms.assetid: 8c349bc4-e6ad-43fa-959e-f29168af35b8
ms.openlocfilehash: 00699f31b821aa508feec9ffe062d768f27ee5a2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50475594"
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

[Ustawianie właściwości klawiszy skrótów](../windows/setting-accelerator-properties.md)<br/>
[Edytor klawiszy skrótów](../windows/accelerator-editor.md)