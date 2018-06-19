---
title: 'Menu i zasoby: dodatki do kontenera | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- IDP_OLE_INIT_FAILED
- IDP_FAILED_TO_CREATE
- VK_ESCAPE
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2c71e8a79652a86ba412ef829ac1151256d1bf65
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33350656"
---
# <a name="menus-and-resources-container-additions"></a>Menu i zasoby: dodatki do kontenera
W tym artykule opisano zmiany, które należy wprowadzić do menu i innych zasobów w programie visual edycji aplikacji kontenera.  
  
 W aplikacjach kontenera, należy wykonać dwa rodzaje zmian: zmian do istniejących zasobów do obsługi edycja wizualna OLE i dodawania nowych zasobów używany do aktywacji w miejscu. Jeśli Kreator aplikacji umożliwia tworzenie aplikacji kontenera, zostaną wykonane następujące kroki dla Ciebie, ale mogą wymagać pewne dostosowania.  
  
 Jeśli nie używasz Kreatora aplikacji, można przyjrzeć się OCLIENT. RC, skrypt zasobu OCLIENT przykładowej aplikacji, aby zobaczyć, jak te zmiany są implementowane. Zobacz przykład MFC OLE [OCLIENT](../visual-cpp-samples.md).  
  
 Omówione w tym artykule tematy obejmują:  
  
-   [Dodatkowe Menu kontenera](#_core_container_menu_additions)  
  
-   [Dodatki do tabeli akceleratora](#_core_container_application_accelerator_table_additions)  
  
-   [Dodatki tabeli ciągów](#_core_string_table_additions_for_container_applications)  
  
##  <a name="_core_container_menu_additions"></a> Dodatkowe Menu kontenera  
 Należy dodać następujące elementy do menu Edycja:  
  
|Element|Cel|  
|----------|-------------|  
|**Wstawianie nowego obiektu**|Otwiera okno dialogowe Wstaw obiekt OLE, aby wstawić element połączony lub osadzony w dokumencie.|  
|**Wklej łącze**|Wkleja łącze do elementu ze Schowka do dokumentu.|  
|**Zlecenie OLE**|Wywołuje primary — zlecenie wybranego elementu. Tekst zmiany elementu menu odzwierciedlają primary — zlecenie wybranego elementu.|  
|**Łącza**|Otwiera okno dialogowe OLE Edytuj łącza, aby zmienić istniejące elementy połączone.|  
  
 Oprócz zmian wymienione w tym artykule pliku źródłowego musi zawierać AFXOLECL. RC, który jest wymagany do wykonania Microsoft Foundation Class Library. Wstaw nowy obiekt jest tylko wymagane menu. Inne elementy do dodania, ale to wymienione w tym miejscu są najczęściej.  
  
 Jeśli chcesz obsługi aktywacji w miejscu z zawartych w niej elementów, należy utworzyć nowego menu aplikacji kontenera. W tym menu składa się z tego samego pliku menu i menu podręcznego okna używany, gdy pliki są otwarte, ale ma dwa separatory się między nimi. Te separatory są używane do wskazywania, gdzie element serwera (składnik) (aplikacja) należy umieścić jego menu po uaktywnieniu w miejscu. Aby uzyskać więcej informacji na temat tej techniki scalania menu, zobacz [menu i zasoby: scalanie Menu](../mfc/menus-and-resources-menu-merging.md).  
  
##  <a name="_core_container_application_accelerator_table_additions"></a> Dodatki tabeli akceleratora do aplikacji kontenera  
 Niewielkie zmiany w zasoby tabeli akceleratora aplikacji kontenera są niezbędne, jeśli aktywacja w miejscu są obsługiwane. Pierwsza zmiana umożliwia użytkownikowi naciśnij klawisz escape (ESC), aby anulować tryb edycji w miejscu. Dodaj następujący wpis do tabeli akceleratora główne:  
  
|ID|Key|Typ|  
|--------|---------|----------|  
|**ID_CANCEL_EDIT_CNTR**|VK_ESCAPE —|**VIRTKEY**|  
  
 Drugi zmiana ma na celu utworzenie nowej tabeli akceleratora umożliwiająca nowego zasobu menu utworzone dla aktywacji w miejscu. Ta tabela ma wpisy dla menu Plik i okno oprócz **vk_escape —** wejścia powyżej. Poniższy przykład jest tabeli akceleratora utworzone dla aktywacji w miejscu w przykładowym MFC [kontenera](../visual-cpp-samples.md):  
  
|ID|Key|Typ|  
|--------|---------|----------|  
|`ID_FILE_NEW`|CTRL + N|**VIRTKEY**|  
|`ID_FILE_OPEN`|CTRL+O|**VIRTKEY**|  
|**ID_FILE_SAVE —**|CTRL+S|**VIRTKEY**|  
|**ID_FILE_PRINT —**|CTRL + P|**VIRTKEY**|  
|**ID_NEXT_PANE —**|VK_F6|**VIRTKEY**|  
|**ID_PREV_PANE —**|SHIFT + VK_F6|**VIRTKEY**|  
|**ID_CANCEL_EDIT_CNTR**|VK_ESCAPE —|**VIRTKEY**|  
  
##  <a name="_core_string_table_additions_for_container_applications"></a> Ciąg tabeli dodatki do aplikacji kontenera  
 Większość zmian do tabel ciągów dla aplikacji kontenera odpowiadają elementów menu dodatkowe wspomnianego [dodatki do kontenera Menu](#_core_container_menu_additions). Dostarczają tekst wyświetlany w pasku stanu wyświetlania każdego elementu menu. Na przykład poniżej przedstawiono wpisów tabeli ciągów, generowanych przez Kreatora aplikacji:  
  
|ID|String|  
|--------|------------|  
|**IDP_OLE_INIT_FAILED —**|Nie można zainicjować interfejsu OLE. Upewnij się, że biblioteki OLE są zainstalowane poprawne wersje.|  
|**IDP_FAILED_TO_CREATE —**|Nie można utworzyć obiektu. Upewnij się, że obiekt jest wprowadzana w rejestrze systemu.|  
  
## <a name="see-also"></a>Zobacz też  
 [Menu i zasoby (OLE)](../mfc/menus-and-resources-ole.md)   
 [Menu i zasoby: dodatki do serwera](../mfc/menus-and-resources-server-additions.md)

