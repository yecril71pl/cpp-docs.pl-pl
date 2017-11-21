---
title: "Właściwość modyfikatora akceleratora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: Modifier property
ms.assetid: f05a9379-e037-4cfb-b6ef-d2c655bcfa7f
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d54c131af740c9c2248c4d923176b0a5c55d9e33
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="accelerator-modifier-property"></a>Właściwość modyfikatora akceleratora
Poniżej przedstawiono prawne wpisy dla właściwości modyfikator w tabeli akceleratora.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|**Brak**|Użytkownik naciska klucz wartość. Najbardziej efektywne służy to wartościami ASCII/ANSI 001 za pośrednictwem 026, który jest interpretowany jako ^ od A do ^ Z (CTRL-A za pomocą klawiszy CTRL-Z).|  
|**ALT**|Użytkownik musi nacisnąć klawisz ALT przed wartością klucza.|  
|**CTRL**|Użytkownik musi naciśnij klawisz CTRL przed wartością klucza. Nieprawidłowy typ ASCII.|  
|**SHIFT**|Użytkownik musi klawisz SHIFT przed wartością klucza.|  
|**Ctrl + Alt**|Użytkownik musi nacisnąć klawisz CTRL i klawisz ALT przed wartością klucza. Nieprawidłowy typ ASCII.|  
|**Ctrl + Shift**|Użytkownik musi nacisnąć klawisz CTRL i SHIFT klucza przed wartością klucza. Nieprawidłowy typ ASCII.|  
|**Alt + Shift**|Użytkownik musi nacisnąć klawisz ALT i klawisz SHIFT przed wartością klucza. Nieprawidłowy typ ASCII.|  
|**Ctrl + Alt + Shift**|Użytkownik musi nacisnąć klawisz CTRL, ALT i SHIFT, przed wartością klucza. Nieprawidłowy typ ASCII.|  
  
## <a name="requirements"></a>Wymagania  
 Win32  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie właściwości klawiszy skrótów](../windows/setting-accelerator-properties.md)   
 [Edytor klawiszy skrótów](../windows/accelerator-editor.md)