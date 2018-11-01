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
ms.openlocfilehash: ea4159f8eb60f43f60eacd5831ce148c81aeb572
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50546617"
---
# <a name="menus-and-resources-container-additions"></a>Menu i zasoby: dodatki do kontenera

W tym artykule opisano zmiany, które należy podjąć, menu i innych zasobów w visual edycję aplikacji kontenera.

W aplikacjach kontenera dwa rodzaje zmian, należy wykonać: modyfikacje do istniejących zasobów do obsługi edycja wizualna OLE i dodawania nowych zasobów używany do aktywacji w miejscu. Jeśli tworzenie aplikacji kontenera za pomocą Kreatora aplikacji, zostaną wykonane następujące kroki dla Ciebie, ale mogą one wymagać dostosowania.

Jeśli nie używasz Kreatora aplikacji, możesz przyjrzeć się OCLIENT. RC, skrypt zasobu OCLIENT przykładowej aplikacji, aby zobaczyć, jak te zmiany są zaimplementowane. Zobacz przykładową MFC OLE [OCLIENT](../visual-cpp-samples.md).

Tematy omówione w tym artykule obejmują:

- [Dodatki do kontenera Menu](#_core_container_menu_additions)

- [Dodatki do tabeli akceleratora](#_core_container_application_accelerator_table_additions)

- [Dodatki tabeli ciągów](#_core_string_table_additions_for_container_applications)

##  <a name="_core_container_menu_additions"></a> Dodatki do kontenera Menu

W menu Edycja, należy dodać następujące elementy:

|Element|Cel|
|----------|-------------|
|**Wstaw nowy obiekt**|Powoduje otwarcie okna dialogowego OLE wprowadź obiekt, aby wstawić osadzony lub połączony element do dokumentu.|
|**Wklej łącze**|Wkleja łącze do elementu ze Schowka do dokumentu.|
|**Zlecenia OLE**|Wywołuje primary — zlecenie wybranego elementu. Tekst tego zmieniony element menu, aby odzwierciedlić primary — zlecenie wybranego elementu.|
|**Łącza**|Otwiera okno dialogowe OLE Edytuj łącza, aby zmienić istniejące elementy połączone.|

Oprócz zmian wymienione w tym artykule pliku źródłowego musi zawierać AFXOLECL. RC, który jest wymagany do wykonania w bibliotece klas Microsoft Foundation. Wstaw nowy obiekt jest tylko wymagane menu. Można dodać inne elementy, ale przedstawionych tutaj są najbardziej rozpowszechnione.

Jeśli chcesz obsługiwać aktywacji w miejscu zawartych w niej elementów, należy utworzyć nowe menu dla aplikacji kontenera. To menu składa się z tym samym menu Plik i menu podręczne okna używany, gdy pliki są otwarte, ale ma dwa separatory znajdująca się między nimi. Separatory te są używane do wskazać, gdzie element serwera (składnik) (aplikacja) należy umieszczać jego menu, gdy aktywowany w miejscu. Aby uzyskać więcej informacji na temat tej techniki scalania menu, zobacz [menu i zasoby: scalanie Menu](../mfc/menus-and-resources-menu-merging.md).

##  <a name="_core_container_application_accelerator_table_additions"></a> Dodawanie tabeli akceleratora aplikacji kontenera

Niewielkie zmiany zasobów Tabela akceleratora aplikacji kontenera są niezbędne, jeśli są obsługiwane aktywacji w miejscu. Pierwsza zmiana umożliwia użytkownikowi naciśnij klawisz ESC (ESC), aby anulować tryb edycji w miejscu. Dodaj następujący wpis do tabeli akceleratora główne:

|ID|Key|Typ|
|--------|---------|----------|
|ID_CANCEL_EDIT_CNTR|VK_ESCAPE —|**VIRTKEY**|

Zmień drugi polega na utworzeniu nowej tabeli akceleratora, który odnosi się do nowego zasobu menu utworzone dla aktywacji w miejscu. Ta tabela zawiera wpisy dla menu Plik i okna, oprócz wpisu vk_escape — powyżej. Poniższy przykład jest tabela akceleratora utworzone dla aktywacji w miejscu, w przykładzie MFC [kontenera](../visual-cpp-samples.md):

|ID|Key|Typ|
|--------|---------|----------|
|ID_FILE_NEW —|CTRL + N|**VIRTKEY**|
|ID_FILE_OPEN —|CTRL+O|**VIRTKEY**|
|ID_FILE_SAVE —|CTRL+S|**VIRTKEY**|
|ID_FILE_PRINT|NACIŚNIJ KLAWISZE CTRL + P|**VIRTKEY**|
|ID_NEXT_PANE —|VK_F6|**VIRTKEY**|
|ID_PREV_PANE —|SHIFT + VK_F6|**VIRTKEY**|
|ID_CANCEL_EDIT_CNTR|VK_ESCAPE —|**VIRTKEY**|

##  <a name="_core_string_table_additions_for_container_applications"></a> Parametry tabeli dodatki dla aplikacji kontenera

Większość zmian do tabel ciągów dla aplikacji kontenera odnoszą się do elementów menu dodatkowych wymienione w [dodatki do kontenera Menu](#_core_container_menu_additions). Dostarczają tekstu wyświetlanego na pasku stanu, gdy każdy element menu jest wyświetlany. Na przykład poniżej przedstawiono wpisów tabeli ciągów, które generuje Kreatora aplikacji:

|ID|String|
|--------|------------|
|IDP_OLE_INIT_FAILED|Zainicjowanie OLE nie powiodło się. Upewnij się, że biblioteki OLE są w poprawnej wersji.|
|IDP_FAILED_TO_CREATE|Nie można utworzyć obiektu. Upewnij się, że obiekt wprowadzono do rejestru systemu.|

## <a name="see-also"></a>Zobacz też

[Menu i zasoby (OLE)](../mfc/menus-and-resources-ole.md)<br/>
[Menu i zasoby: dodatki do serwera](../mfc/menus-and-resources-server-additions.md)

