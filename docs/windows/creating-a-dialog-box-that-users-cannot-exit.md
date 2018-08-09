---
title: Tworzenie okna dialogowego, którego nie można zamknąć | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: b176fbc4e420c08a2262b532cf1310ada56c978a
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39644183"
---
# <a name="creating-a-dialog-box-that-users-cannot-exit"></a>Tworzenie okna dialogowego, którego użytkownik nie może zamknąć
Można utworzyć użytkownika nie może zamknąć okno dialogowe z środowiska uruchomieniowego. Tego rodzaju okno dialogowe jest użyteczny ze względu na potrzeby logowania oraz dla aplikacji lub blokady dokumentu.  
  
### <a name="to-create-a-dialog-box-that-a-user-cannot-exit"></a>Aby utworzyć okno dialogowe, które użytkownik nie może zamknąć  
  
1.  W **właściwości** okienku okna dialogowego, ustaw **Menu systemowe** właściwości **false**.  
  
     Powoduje to wyłączenie menu systemu okna dialogowego i **Zamknij** przycisku.  
  
2.  W formularzu okno dialogowe Usuń **anulować** i **OK** przycisków.  
  
     W czasie wykonywania użytkownik nie może zamknąć okno modalne okno dialogowe, które ma te cechy.  
  
 Umożliwia testowanie tego rodzaju okno dialogowe funkcji okno dialogowe testowej wykrywa, gdy **Esc** naciśnięciu. (**Esc** jest również nazywany vk_escape — klawisz wirtualnego.) Niezależnie od tego, jak okno dialogowe umożliwia zachowanie w czasie wykonywania, możesz zakończyć je w trybie testowym, naciskając klawisz **Esc**.  
  
> [!NOTE]
>  Dla aplikacji MFC, aby utworzyć okno dialogowe, którego nie można zamknąć, należy zastąpić domyślne zachowanie `OnOK` i `OnCancel` ponieważ nawet wtedy, gdy usuniesz skojarzone przyciski, nadal można odrzucić okno dialogowe, naciskając klawisz  **Wprowadź** lub **Esc**.  
  
 Aby uzyskać informacje dotyczące sposobu dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index).  
  
## <a name="requirements"></a>Wymagania  
 Win32  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: tworzenie zasobu](../windows/how-to-create-a-resource.md)   
 [Pliki zasobów](../windows/resource-files-visual-studio.md)   
 [Edytor okien dialogowych](../windows/dialog-editor.md)