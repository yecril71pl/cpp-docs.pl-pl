---
title: 'Schowek: korzystanie ze schowka systemu Windows'
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
ms.openlocfilehash: 1b11bfe18443858de0dd7032f72fecadb1d6ebdd
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626036"
---
# <a name="clipboard-using-the-windows-clipboard"></a>Schowek: korzystanie ze schowka systemu Windows

W tym temacie opisano sposób używania standardowego interfejsu API Schowka systemu Windows w aplikacji MFC.

Większość aplikacji dla systemu Windows obsługuje wycinanie lub kopiowanie danych do Schowka systemu Windows i wklejanie danych ze schowka. Formaty danych schowka różnią się w zależności od aplikacji. Platforma obsługuje tylko ograniczoną liczbę formatów Schowka dla ograniczonej liczby klas. Zwykle wdrażane są polecenia dotyczące schowka — wycinanie, kopiowanie i wklejanie — w menu Edycja widoku. Biblioteka klas definiuje identyfikatory poleceń następujących poleceń: **ID_EDIT_CUT**, **ID_EDIT_COPY**i **ID_EDIT_PASTE**. Są również zdefiniowane monity wiersza wiadomości.

[Komunikaty i polecenia w strukturze](messages-and-commands-in-the-framework.md) wyjaśniają, jak obsłużyć polecenia menu w aplikacji, mapując polecenie menu do funkcji obsługi. Tak długo, jak aplikacja nie definiuje funkcji obsługi dla poleceń Schowka w menu Edycja, pozostaną wyłączone. Aby napisać funkcje obsługi dla poleceń wycinania i kopiowania, zaimplementuj wybór w aplikacji. Aby napisać funkcję procedury obsługi dla polecenia Wklej, zbadaj schowek, aby zobaczyć, czy zawiera on dane w formacie, który aplikacja może zaakceptować. Na przykład, aby włączyć polecenie copy, można napisać procedurę obsługi podobną do następującej:

[!code-cpp[NVC_MFCListView#2](../atl/reference/codesnippet/cpp/clipboard-using-the-windows-clipboard_1.cpp)]

Polecenia wycinania, kopiowania i wklejania są zrozumiałe tylko w niektórych kontekstach. Polecenia wycinania i kopiowania powinny być włączone tylko wtedy, gdy coś jest zaznaczone, a polecenie Wklej tylko wtedy, gdy coś znajduje się w Schowku. To zachowanie można zapewnić, definiując funkcje programu obsługi aktualizacji, które włączają lub wyłączają te polecenia w zależności od kontekstu. Aby uzyskać więcej informacji, zobacz [jak zaktualizować obiekty interfejsu użytkownika](how-to-update-user-interface-objects.md).

Biblioteka MFC zapewnia obsługę Schowka na potrzeby edycji tekstu przy użyciu `CEdit` klas i `CEditView` . Klasy OLE upraszczają także implementowanie operacji schowka, które obejmują elementy OLE. Aby uzyskać więcej informacji na temat klas OLE, zobacz [schowek: korzystanie z mechanizmu Schowka OLE](clipboard-using-the-ole-clipboard-mechanism.md).

Zaimplementowanie innych poleceń menu edycji, takich jak Cofnij (**ID_EDIT_UNDO**) i wykonaj ponownie (**ID_EDIT_REDO**), również pozostało do Ciebie. Jeśli aplikacja nie obsługuje tych poleceń, można je łatwo usunąć z pliku zasobów przy użyciu edytorów zasobów Visual C++.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o

- [kopiowanie i wklejanie danych](clipboard-copying-and-pasting-data.md)

- [Korzystanie z mechanizmu Schowka OLE](clipboard-using-the-ole-clipboard-mechanism.md)

## <a name="see-also"></a>Zobacz też

[Schowek](clipboard.md)
