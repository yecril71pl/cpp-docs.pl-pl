---
title: Dodawanie klasy MFC
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.classes.adding.mfc
helpviewer_keywords:
- classes [MFC], adding MFC
- MFC, adding classes
ms.assetid: 9a96b67f-40bf-43d4-8872-2f8dfc5404f1
ms.openlocfilehash: 1cc3dc734917da46af99e67da40fe243941102e3
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57280670"
---
# <a name="adding-an-mfc-class"></a>Dodawanie klasy MFC

Aby dodać klasy pochodne od klas biblioteki Microsoft Foundation Class (MFC) do projektu, należy użyć **Dodaj klasę** polecenia dostępne [Widok klas](/visualstudio/ide/viewing-the-structure-of-code). Określ nazwę dla nowej klasy, wybierz klasę bazową, a następnie wybierz identyfikator okna dialogowego, z którą jest skojarzony (jeśli istnieje). Kreator kod tworzy plik nagłówka i pliku z implementacją i dodaje je do projektu.

> [!NOTE]
>  Klasy MFC można dodawać do aplikacji ATL COM, jeśli można początkowo [tworzenia aplikacji z obsługą MFC](../../atl/reference/mfc-support-in-atl-projects.md). Klasy MFC można również dodać do projekty Win32, które obsługują MFC.

### <a name="to-add-an-mfc-class-to-your-project"></a>Dodawanie klasy MFC do projektu

1. W widoku klas kliknij prawym przyciskiem myszy nazwę projektu. Kliknij przycisk **Dodaj** a następnie kliknij przycisk **Dodaj klasę** otworzyć [Dodaj klasę](../../ide/add-class-dialog-box.md) okno dialogowe.

1. W okienku szablonów zaznacz **klasy MFC** i naciśnij klawisz **Dodaj** przycisku.

1. Zdefiniuj ustawienia dla nowej klasy w [Kreator klas MFC](../../mfc/reference/mfc-add-class-wizard.md) okno dialogowe.

1. Kliknij przycisk **Zakończ** aby zamknąć kreatora i wyświetlić nową klasę w widoku klas. Można również wyświetlić pliki tworzone przez kreatora w **Eksploratora rozwiązań**.

## <a name="see-also"></a>Zobacz także

[Dodawanie funkcji za pomocą kreatorów kodu](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Dodawanie klasy](../../ide/adding-a-class-visual-cpp.md)<br/>
[Klasa — Przegląd](../../mfc/class-library-overview.md)
