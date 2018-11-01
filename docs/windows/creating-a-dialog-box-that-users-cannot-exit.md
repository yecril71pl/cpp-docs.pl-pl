---
title: Tworzenie okna dialogowego (C++), którego użytkownik nie może zamknąć
ms.date: 11/04/2016
helpviewer_keywords:
- dialog boxes [C++], creating
- modal dialog boxes [C++], logon screens
- logon screens
ms.assetid: 54823c27-1658-4388-bd12-0a1ce8f3899e
ms.openlocfilehash: 83c6c099f3d39db66969371e2cf7ad99a7f08587
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50579845"
---
# <a name="creating-a-dialog-box-c-that-users-cannot-exit"></a>Tworzenie okna dialogowego (C++), którego użytkownik nie może zamknąć

Można utworzyć użytkownika nie może zamknąć okno dialogowe z środowiska uruchomieniowego. Tego rodzaju okno dialogowe jest użyteczny ze względu na potrzeby logowania oraz dla aplikacji lub blokady dokumentu.

### <a name="to-create-a-dialog-box-that-a-user-cannot-exit"></a>Aby utworzyć okno dialogowe, które użytkownik nie może zamknąć

1. W **właściwości** okienku okna dialogowego, ustaw **Menu systemowe** właściwości **false**.

   Powoduje to wyłączenie menu systemu okna dialogowego i **Zamknij** przycisku.

2. W formularzu okno dialogowe Usuń **anulować** i **OK** przycisków.

   W czasie wykonywania użytkownik nie może zamknąć okno modalne okno dialogowe, które ma te cechy.

Umożliwia testowanie tego rodzaju okno dialogowe funkcji okno dialogowe testowej wykrywa, gdy **Esc** naciśnięciu. (**Esc** jest również nazywany vk_escape — klawisz wirtualnego.) Niezależnie od tego, jak okno dialogowe umożliwia zachowanie w czasie wykonywania, możesz zakończyć je w trybie testowym, naciskając klawisz **Esc**.

> [!NOTE]
> Dla aplikacji MFC, aby utworzyć okno dialogowe, którego nie można zamknąć, należy zastąpić domyślne zachowanie `OnOK` i `OnCancel` ponieważ nawet wtedy, gdy usuniesz skojarzone przyciski, nadal można odrzucić okno dialogowe, naciskając klawisz  **Wprowadź** lub **Esc**.

Aby uzyskać informacje dotyczące sposobu dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index).

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Instrukcje: tworzenie zasobu](../windows/how-to-create-a-resource.md)<br/>
[Pliki zasobów](../windows/resource-files-visual-studio.md)<br/>
[Edytor okien dialogowych](../windows/dialog-editor.md)