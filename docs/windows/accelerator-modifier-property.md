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
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 63d6a4b526fc1f2aeb2a942e682a8c7cc6f9b58c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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