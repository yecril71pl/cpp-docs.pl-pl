---
title: Właściwość typu akceleratora | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: da825a4f2052f05b24ff724d709c7c8a4b6a3db3
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39645688"
---
# <a name="accelerator-type-property"></a>Właściwość typu akceleratora
Akcelerator **typu** właściwość określa, czy klawisz skrótu skojarzony identyfikator akceleratora jest wirtualny kombinacji klawiszy lub ASCII/ANSI wartość klucza:  
  
-   Jeśli **typu** właściwość jest ASCII, [modyfikator](../windows/accelerator-modifier-property.md) może składać się wyłącznie `None` lub `Alt`, lub może być akceleratora, który używa **Ctrl** (określony przez klucz klucza z poprzednich `^`).  
  
-   Jeśli **typu** właściwość jest VIRTKEY i dowolną kombinację `Modifier` i `Key` wartości jest prawidłowy.  
  
    > [!NOTE]
    >  Jeśli chcesz wprowadzić wartość w tabeli akceleratora i wartości traktowane jak ASCII/ANSI, po prostu kliknij **typu** wpisu w tabeli i ASCII wybierz z listy rozwijanej. Jednak jeśli używasz **dalej wpisany klucz** polecenia (**Edytuj** menu) do określenia `Key`, należy zmienić **typu** właściwość VIRTKEY ASCII *przed* wprowadzania `Key` kodu.  
  
## <a name="requirements"></a>Wymagania  
 Win32  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie właściwości klawiszy skrótów](../windows/setting-accelerator-properties.md)   
 [Edytor klawiszy skrótów](../windows/accelerator-editor.md)