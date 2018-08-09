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
ms.openlocfilehash: 0788536e776661b9a84a6cccc648a7db68389ae5
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39644258"
---
# <a name="accelerator-modifier-property"></a>Właściwość modyfikatora akceleratora
Dostępne są następujące wpisy prawne dla właściwości modyfikujące w tabeli akceleratora.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|**Brak**|Użytkownik naciśnie tylko **klucz** wartość. Najbardziej efektywne służy to przy użyciu wartości ASCII/ANSI 001 za pośrednictwem 026, który jest interpretowany jako ^ od A do ^ Z (CTRL-A za pomocą klawisze CTRL + Z).|  
|**ALT**|Użytkownik musi nacisnąć klawisz **Alt** klucza przed **klucz** wartość.|  
|**CTRL**|Użytkownik musi nacisnąć klawisz **Ctrl** klucza przed **klucz** wartość. Nie jest prawidłowy z typem ASCII.|  
|**SHIFT**|Użytkownik musi nacisnąć klawisz **Shift** klucza przed **klucz** wartość.|  
|**Ctrl + Alt**|Użytkownik musi nacisnąć klawisz **Ctrl** klucza i **Alt** klucza przed **klucz** wartość. Nie jest prawidłowy z typem ASCII.|  
|**Ctrl + Shift**|Użytkownik musi nacisnąć klawisz **Ctrl** klucza i **Shift** klucza przed **klucz** wartość. Nie jest prawidłowy z typem ASCII.|  
|**Alt + Shift**|Użytkownik musi nacisnąć klawisz **Alt** klucza i **Shift** klucza przed **klucz** wartość. Nie jest prawidłowy z typem ASCII.|  
|**Ctrl + Alt + Shift**|Użytkownik musi nacisnąć klawisz **Ctrl**, **Alt**, i **Shift** przed **klucz** wartość. Nie jest prawidłowy z typem ASCII.|  
  
## <a name="requirements"></a>Wymagania  
 Win32  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie właściwości klawiszy skrótów](../windows/setting-accelerator-properties.md)   
 [Edytor klawiszy skrótów](../windows/accelerator-editor.md)