---
title: 'Schowek: Korzystanie ze Schowka systemu Windows | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6063a27495d46e4b54f3133b92689e4b0faaa631
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="clipboard-using-the-windows-clipboard"></a>Schowek: korzystanie ze schowka systemu Windows
W tym temacie opisano sposób użycia standardowy interfejs API schowka systemu Windows w aplikacji MFC.  
  
 Większość aplikacji dla systemu Windows obsługuje wycinanie i kopiowanie danych do Schowka systemu Windows i wklejanie danych ze Schowka. Różne formaty danych schowka między aplikacjami. Platforma obsługuje ograniczoną liczbę formatów Schowka dla ograniczonej liczby klas. Zwykle wdroży polecenia związane z Schowka — wycinania, kopiowania i wklejania — menu Edycja widoku. Biblioteka klas definiuje identyfikatory poleceń dla tych poleceń: **id_edit_cut —**, **id_edit_copy —**, i **id_edit_paste —**. Można zdefiniować ich monity Wiersz wiadomości.  
  
 [Komunikaty i polecenia w strukturze](../mfc/messages-and-commands-in-the-framework.md) wyjaśniono sposób obsługi przez mapowanie polecenia menu funkcji programu obsługi poleceń menu w aplikacji. Tak długo, jak aplikacja nie ma zdefiniowanej funkcje programu obsługi dla poleceń Schowka w menu Edycja, pozostaną one wyłączone. Aby napisać funkcje programu obsługi poleceń Wytnij i Kopiuj, zaimplementować zaznaczenia w aplikacji. Aby napisać funkcję obsługi polecenia Wklej, zapytania Schowka, aby zobaczyć, czy zawiera on dane w formacie, który może zaakceptować aplikację. Na przykład aby włączyć polecenia Kopiuj, można napisać obsługi postać zbliżoną do następującej:  
  
 [!code-cpp[NVC_MFCListView#2](../atl/reference/codesnippet/cpp/clipboard-using-the-windows-clipboard_1.cpp)]  
  
 Polecenia wycinania, kopiowania i wklejania tylko są przydatne w niektórych kontekstach. Polecenia Wytnij i Kopiuj powinna być włączona tylko wtedy, gdy element jest zaznaczony, a polecenie Wklej tylko wtedy, gdy coś jest w Schowku. Musisz podać to zachowanie, definiując funkcje programu obsługi aktualizacji, które włączyć lub wyłączyć tych poleceń, w zależności od kontekstu. Aby uzyskać więcej informacji, zobacz [jak obiekty interfejsu użytkownika aktualizacji](../mfc/how-to-update-user-interface-objects.md).  
  
 Microsoft Foundation Class Library zapewnić obsługę Schowka do edycji tekstu z `CEdit` i `CEditView` klasy. Klasy OLE również uprościć implementującej operacje schowka, które obejmuje elementy OLE. Aby uzyskać więcej informacji na temat klas OLE, zobacz [Schowek: Korzystanie z mechanizmu Schowka OLE](../mfc/clipboard-using-the-ole-clipboard-mechanism.md).  
  
 Implementowanie innych edytować polecenia menu, takie jak cofania (**id_edit_undo —**) i wykonaj ponownie (**id_edit_redo —**), również pozostało do Ciebie. Jeśli aplikacja nie obsługuje tych poleceń, można z łatwością usunąć je z pliku zasobów przy użyciu edytory zasobów programu Visual C++.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o  
  
-   [Kopiowanie i wklejanie danych](../mfc/clipboard-copying-and-pasting-data.md)  
  
-   [Korzystanie z mechanizmu Schowka OLE](../mfc/clipboard-using-the-ole-clipboard-mechanism.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Schowek](../mfc/clipboard.md)

