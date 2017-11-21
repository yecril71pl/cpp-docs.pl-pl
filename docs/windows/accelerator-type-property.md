---
title: "Właściwość typu akceleratora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Type property
- VIRTKEY
ms.assetid: 8c349bc4-e6ad-43fa-959e-f29168af35b8
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ef1788f451597cdc8d3b512f5eede3c3d5abb382
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="accelerator-type-property"></a>Właściwość typu akceleratora
Akceleratora **typu** właściwość określa, czy klawisz skrótu skojarzony z Identyfikatorem akceleratora kombinację klawiszy wirtualnych lub ASCII/ANSI wartość klucza:  
  
-   Jeśli **typu** właściwość jest **ASCII**, [modyfikator](../windows/accelerator-modifier-property.md) mogą być tylko None lub Alt, albo może mieć akceleratora, który używa klawisz CTRL (określony za pomocą klucza o poprzedzających ^).  
  
-   Jeśli **typu** właściwość jest **VIRTKEY**, dowolnej kombinacji wartości modyfikator i klucz jest nieprawidłowy.  
  
    > [!NOTE]
    >  Jeśli chcesz wprowadzić wartości w tabeli akceleratora i mają być traktowane jako ASCII/ANSI wartości, po prostu kliknij typ wpisu w tabeli i ASCII wybierz z listy rozwijanej. Jednak jeśli używasz **dalej wpisany klucz** polecenia (**Edytuj** menu) do określenia klucza, należy zmienić **typu** właściwości z VIRTKEY ASCII *przed* wprowadzenie kodu klucza.  
  
## <a name="requirements"></a>Wymagania  
 Win32  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie właściwości klawiszy skrótów](../windows/setting-accelerator-properties.md)   
 [Edytor klawiszy skrótów](../windows/accelerator-editor.md)