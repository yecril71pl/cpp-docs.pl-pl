---
title: 'Schowek: Korzystanie ze Schowka Windows'
ms.date: 11/04/2016
helpviewer_keywords:
- Clipboard commands
- Cut/Copy and Paste command handler functions [MFC]
- handler functions, Cut/Copy and Paste commands
- Clipboard [MFC], commands
- commands [MFC], implementing Edit
- Clipboard commands [MFC], implementing
- Windows Clipboard [MFC]
- Clipboard [MFC], Windows Clipboard API
ms.assetid: 24415b42-9301-4a70-b69a-44c97918319f
ms.openlocfilehash: 49111e4efd2a12264d61030fe038d80b974514c1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62326992"
---
# <a name="clipboard-using-the-windows-clipboard"></a>Schowek: Korzystanie ze Schowka Windows

W tym temacie opisano sposób używania standardowych Windows Schowka interfejsu API w aplikacji MFC.

Większość aplikacji dla Windows obsługuje wycinanie i kopiowanie danych do Schowka Windows i wklejanie danych ze Schowka. Formaty danych schowka różnią się między aplikacjami. Platforma obsługuje tylko ograniczoną liczbę formaty Schowka dla ograniczonej liczby klas. Zwykle wdroży polecenia związane z Schowka — wycinania, kopiowania i wklejania — menu Edycja widoku. Biblioteka klas definiuje identyfikatory poleceń dla tych poleceń: **Id_edit_cut —**, **id_edit_copy —**, i **id_edit_paste —**. Monity o ich wiersz wiadomości są również określone.

[Komunikaty i polecenia w ramach](../mfc/messages-and-commands-in-the-framework.md) wyjaśnia sposób obsługi polecenia menu w aplikacji przez mapowanie polecenie menu do funkcji obsługi. Tak długo, jak aplikacja nie definiuje funkcji obsługi dla poleceń Schowka w menu Edycja, pozostaną one wyłączone. Do pisania funkcji obsługi poleceń Wytnij i Kopiuj, należy zaimplementować zaznaczenia w aplikacji. Do pisania funkcji procedury obsługi polecenia wklejania, Wyślij zapytanie do Schowka, aby zobaczyć, czy zawiera on dane w formacie, które aplikacja może akceptować. Na przykład aby włączyć polecenia Kopiuj, można napisać program obsługi podobny do poniższego:

[!code-cpp[NVC_MFCListView#2](../atl/reference/codesnippet/cpp/clipboard-using-the-windows-clipboard_1.cpp)]

Polecenia wycinanie, kopiowanie i wklejanie tylko są istotne w określonych kontekstach. Polecenia Wytnij i Kopiuj powinno być włączone, tylko wtedy, gdy coś jest zaznaczone, a polecenie Paste tylko wtedy, gdy coś jest w Schowku. To zachowanie można podać, definiując funkcje programu obsługi aktualizacji, które włączać lub wyłączać tych poleceń, w zależności od kontekstu. Aby uzyskać więcej informacji, zobacz [jak obiektów interfejsu użytkownika aktualizacji](../mfc/how-to-update-user-interface-objects.md).

Bibliotekę Microsoft Foundation Class obsługi schowka do edycji tekstu za pomocą `CEdit` i `CEditView` klasy. Klasy OLE również uprościć implementującej operacje na schowku obejmujące elementów OLE. Aby uzyskać więcej informacji na temat klasy OLE, zobacz [Schowka: Korzystanie z mechanizmu Schowka OLE](../mfc/clipboard-using-the-ole-clipboard-mechanism.md).

Implementowanie innych edytować polecenia menu, takie jak cofanie (**id_edit_undo —**) i wykonaj ponownie (**id_edit_redo —**), również pozostało do Ciebie. Jeśli aplikacja nie obsługuje tych poleceń, można łatwo usuwać je z pliku zasobów za pomocą edytory zasobów Visual C++.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat

- [Kopiowanie i wklejanie danych](../mfc/clipboard-copying-and-pasting-data.md)

- [Korzystanie z mechanizmu Schowka OLE](../mfc/clipboard-using-the-ole-clipboard-mechanism.md)

## <a name="see-also"></a>Zobacz także

[Schowek](../mfc/clipboard.md)
