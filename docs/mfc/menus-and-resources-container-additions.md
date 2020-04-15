---
title: 'Menu i zasoby: dodatki do kontenera'
ms.date: 11/04/2016
f1_keywords:
- IDP_OLE_INIT_FAILED
- IDP_FAILED_TO_CREATE
- VK_ESCAPE
helpviewer_keywords:
- application accelerator table [MFC]
- VK_ESCAPE key [MFC]
- IDP_FAILED_TO_CREATE macro [MFC]
- visual editing, application menus and resources
- OLE containers [MFC], menus and resources
- accelerator tables [MFC], container applications
- IDP_OLE_INIT_FAILED macro [MFC]
- CONTAIN tutorial [MFC]
- Links menu item [MFC]
ms.assetid: 425448be-8ca0-412e-909a-a3a9ce845288
ms.openlocfilehash: c8da58316f471f7b7d26e142cc1dd1ccaa6ad8b5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364791"
---
# <a name="menus-and-resources-container-additions"></a>Menu i zasoby: dodatki do kontenera

W tym artykule opisano zmiany, które należy włożyć do menu i innych zasobów w aplikacji kontenera edycji wizualnej.

W aplikacjach kontenera należy wprowadzić dwa typy zmian: modyfikacje istniejących zasobów w celu obsługi edycji wizualnej OLE i dodanie nowych zasobów używanych do aktywacji w miejscu. Jeśli używasz kreatora aplikacji do tworzenia aplikacji kontenera, te kroki zostaną wykonane dla Ciebie, ale mogą wymagać pewnego dostosowania.

Jeśli nie używasz kreatora aplikacji, możesz chcieć przyjrzeć się OCLIENT. RC, skrypt zasobów dla przykładowej aplikacji OCLIENT, aby zobaczyć, jak te zmiany są implementowane. Zobacz przykład ole MFC [OCLIENT](../overview/visual-cpp-samples.md).

Tematy omówione w tym artykule obejmują:

- [Dodatki do menu kontenera](#_core_container_menu_additions)

- [Dodatki tabeli akceleratora](#_core_container_application_accelerator_table_additions)

- [Dodatki do tabel ciągów](#_core_string_table_additions_for_container_applications)

## <a name="container-menu-additions"></a><a name="_core_container_menu_additions"></a>Dodatki do menu kontenera

Do menu Edycja należy dodać następujące elementy:

|Element|Przeznaczenie|
|----------|-------------|
|**Wstaw nowy obiekt**|Otwiera okno dialogowe Wstawianie obiektu OLE w celu wstawienia elementu połączonego lub osadzonego do dokumentu.|
|**Wklej łącze**|Wkleja łącze do elementu w Schowku do dokumentu.|
|**Czasownik OLE**|Wywołuje zlecenie podstawowe wybranego elementu. Tekst tego elementu menu zmienia się, aby odzwierciedlić zlecenie podstawowe zaznaczonego elementu.|
|**Linki**|Otwiera okno dialogowe Edycja ole łącza, aby zmienić istniejące połączone elementy.|

Oprócz zmian wymienionych w tym artykule, plik źródłowy musi zawierać AFXOLECL. RC, który jest wymagany dla implementacji biblioteki klas programu Microsoft Foundation. Wstaw nowy obiekt jest jedynym wymaganym dodatkiem menu. Inne elementy można dodać, ale te wymienione tutaj są najczęściej.

Należy utworzyć nowe menu dla aplikacji kontenera, jeśli chcesz obsługiwać aktywację w miejscu zawartych elementów. To menu składa się z tego samego menu Plik i menu podręcznego Okno używane, gdy pliki są otwarte, ale ma dwa separatory umieszczone między nimi. Separatory te służą do wskazania, gdzie element serwera (składnika) (aplikacja) powinien umieszczać swoje menu po uaktywnieniu w miejscu. Aby uzyskać więcej informacji na temat tej techniki scalania menu, zobacz [Menu i Zasoby: Scalanie menu](../mfc/menus-and-resources-menu-merging.md).

## <a name="container-application-accelerator-table-additions"></a><a name="_core_container_application_accelerator_table_additions"></a>Dodatki tabeli akceleratora aplikacji kontenera

Małe zmiany w zasobach tabeli akceleratora aplikacji kontenera są niezbędne, jeśli obsługujesz aktywację w miejscu. Pierwsza zmiana umożliwia użytkownikowi naciśnięcie klawisza ewakuacyjnego (ESC), aby anulować tryb edycji w miejscu. Dodaj następujący wpis do tabeli akceleratora głównego:

|ID|Klucz|Typ|
|--------|---------|----------|
|ID_CANCEL_EDIT_CNTR|VK_ESCAPE|**Virtkey**|

Drugą zmianą jest utworzenie nowej tabeli akceleratora, która odpowiada nowemu zasobowi menu utworzonemu do aktywacji w miejscu. W tej tabeli oprócz powyższ VK_ESCAPEego znajdują się pozycje menu Plik i Okno. Poniższy przykład przedstawia tabelę akceleratora utworzoną dla aktywacji w miejscu w przykładowym [kontenerze](../overview/visual-cpp-samples.md)MFC:

|ID|Klucz|Typ|
|--------|---------|----------|
|ID_FILE_NEW|CTRL+N|**Virtkey**|
|ID_FILE_OPEN|CTRL+O|**Virtkey**|
|Id_file_save|CTRL+S|**Virtkey**|
|ID_FILE_PRINT|CTRL+P|**Virtkey**|
|ID_NEXT_PANE|VK_F6|**Virtkey**|
|ID_PREV_PANE|VK_F6 SHIFT+|**Virtkey**|
|ID_CANCEL_EDIT_CNTR|VK_ESCAPE|**Virtkey**|

## <a name="string-table-additions-for-container-applications"></a><a name="_core_string_table_additions_for_container_applications"></a>Dodatki tabeli ciągów dla aplikacji kontenerowych

Większość zmian w tabelach ciągów dla aplikacji kontenerowych odpowiada dodatkowym elementom menu wymienionym w [dodatkach menu kontenerów](#_core_container_menu_additions). Dostarczają one tekst wyświetlany na pasku stanu, gdy każdy element menu jest wyświetlany. Na przykład oto wpisy tabeli ciągów generowane przez kreatora aplikacji:

|ID|Ciąg|
|--------|------------|
|IDP_OLE_INIT_FAILED|Inicjowanie OLE nie powiodło się. Upewnij się, że biblioteki OLE są poprawną wersją.|
|IDP_FAILED_TO_CREATE|Nie można utworzyć obiektu. Upewnij się, że obiekt został wprowadzony do rejestru systemowego.|

## <a name="see-also"></a>Zobacz też

[Menu i zasoby (OLE)](../mfc/menus-and-resources-ole.md)<br/>
[Menu i zasoby: dodatki do serwera](../mfc/menus-and-resources-server-additions.md)
