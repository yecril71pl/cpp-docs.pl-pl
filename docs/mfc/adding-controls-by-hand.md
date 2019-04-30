---
title: Ręczne dodawanie formantów
ms.date: 11/04/2016
helpviewer_keywords:
- Windows common controls [MFC], adding
- dialog box controls [MFC], adding to dialog boxes
- controlling input focus
- input focus control
- focus, controlling input [MFC]
- controls [MFC], adding to dialog boxes
- common controls [MFC], adding
ms.assetid: bc843e59-0c51-4b5b-8bf2-343f716469d2
ms.openlocfilehash: c70539b49fcf2aa87f0bee375a87b38277b6ed42
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62394809"
---
# <a name="adding-controls-by-hand"></a>Ręczne dodawanie formantów

Możesz albo [dodawanie formantów do okna dialogowego za pomocą edytora okien dialogowych](../mfc/using-the-dialog-editor-to-add-controls.md) lub dodać je samodzielnie, przy użyciu kodu.

Aby utworzyć obiekt formantu samodzielnie, zwykle nastąpi osadzenie C++ obiekt formantu w oknie dialogowym C++ lub obiekt okna ramki. Podobnie jak wiele innych obiektów w ramach formanty wymagają dwuetapowa konstrukcja. Należy wywołać formantu **Utwórz** funkcja elementu członkowskiego jako część tworzenia okna dialogowego pola lub ramki okno nadrzędne. Dla okien dialogowych, to zwykle odbywa się w [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)i okien ramowych w [OnCreate](../mfc/reference/cwnd-class.md#oncreate).

W poniższym przykładzie pokazano, jak może deklarować `CEdit` obiektu w deklaracji klasy, klasy pochodnej okna dialogowego, a następnie wywołać `Create` funkcji składowej we `OnInitDialog`. Ponieważ `CEdit` obiekt nie został zadeklarowany jako obiekt osadzony, jest automatycznie tworzony, gdy jest konstruowany obiektu okna dialogowego, ale nadal musi zostać zainicjowany z jego własnej `Create` funkcja elementu członkowskiego.

[!code-cpp[NVC_MFCControlLadenDialog#1](../mfc/codesnippet/cpp/adding-controls-by-hand_1.h)]

Następujące `OnInitDialog` funkcja konfiguruje prostokąt, następnie wywołuje `Create` utworzyć Windows formantu edycyjnego i dołączyć go do niezainicjowanego `CEdit` obiektu.

[!code-cpp[NVC_MFCControlLadenDialog#2](../mfc/codesnippet/cpp/adding-controls-by-hand_2.cpp)]

Po utworzeniu obiektu edycji można również ustawić fokusu wprowadzania do formantu, wywołując `SetFocus` funkcja elementu członkowskiego. Na koniec Zwróć 0 z `OnInitDialog` aby pokazać, że ustawiony fokus. Po powrocie wartość różną od zera Menedżera okna dialogowego Ustawia fokus na pierwszy element formantu listy elementów w oknie dialogowym. W większości przypadków należy dodać formanty do swojej okien dialogowych za pomocą edytora okien dialogowych.

## <a name="see-also"></a>Zobacz także

[Tworzenie i używanie kontrolek](../mfc/making-and-using-controls.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)<br/>
[CDialog::OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)
