---
title: Tworzenie użytkowników nie może zamknąć okno dialogowe | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- dialog boxes, creating
- modal dialog boxes, logon screens
- logon screens
ms.assetid: 54823c27-1658-4388-bd12-0a1ce8f3899e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fc04c9ccfb0fdc74e57142bf746681411bbba495
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33884466"
---
# <a name="creating-a-dialog-box-that-users-cannot-exit"></a>Tworzenie okna dialogowego, którego użytkownik nie może zamknąć
Można utworzyć środowiska uruchomieniowego okno dialogowe, którego użytkownik nie może zamknąć. Tego rodzaju okno dialogowe jest przydatne do logowania i aplikacji lub blokad dokumentu.  
  
### <a name="to-create-a-dialog-box-that-a-user-cannot-exit"></a>Aby utworzyć okno dialogowe, którego użytkownik nie może zamknąć  
  
1.  W **właściwości** ustawić okienku okna dialogowego **Menu systemowe** właściwości **false**.  
  
     Powoduje wyłączenie menu systemu okna dialogowego i **Zamknij** przycisku.  
  
2.  W formularzu — okno dialogowe Usuwanie **anulować** i **OK** przycisków.  
  
     W czasie wykonywania użytkownik nie może zamknąć modalne okno dialogowe ma następujące cechy.  
  
 Aby umożliwić testowanie tego rodzaju — okno dialogowe, funkcja pole okna dialogowego test wykrywa po naciśnięciu klawisza ESC. (ESC jest nazywane również vk_escape — klawisz wirtualnego). Niezależnie od tego, jak okno dialogowe ma zachowywać się w czasie wykonywania należy zakończyć go w trybie testowym, naciskając klawisz ESC.  
  
> [!NOTE]
>  Dla aplikacji MFC, aby utworzyć okno dialogowe, którego nie można zakończyć użytkowników, należy zastąpić domyślne zachowanie `OnOK` i `OnCancel` ponieważ nawet wtedy, gdy należy usunąć skojarzony przycisków, okno dialogowe nadal może być ukryty, naciskając klawisz ENTER lub ESC.  
  
 Aby uzyskać informacje o tym, jak dodać zasoby do projektów zarządzanych, zobacz [zasobów w aplikacjach pulpitu](/dotnet/framework/resources/index).  
  
## <a name="requirements"></a>Wymagania  
 Win32  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: tworzenie zasobu](../windows/how-to-create-a-resource.md)   
 [Pliki zasobów](../windows/resource-files-visual-studio.md)   
 [Edytor okien dialogowych](../windows/dialog-editor.md)

