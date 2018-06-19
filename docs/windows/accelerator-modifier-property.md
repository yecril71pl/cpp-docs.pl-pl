---
title: Właściwość modyfikatora akceleratora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Modifier property
ms.assetid: f05a9379-e037-4cfb-b6ef-d2c655bcfa7f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d99d4656f2835f9adb60f310e429c4ccb97ac7b6
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33854057"
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