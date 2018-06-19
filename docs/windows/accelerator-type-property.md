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
ms.openlocfilehash: cb1ba8f117fadab7cccb835ba8889d57bcc9f184
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33856504"
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