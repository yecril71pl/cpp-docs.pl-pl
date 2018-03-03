---
title: "Zdefiniowane przez użytkownika narzędzia | Dokumentacja firmy Microsoft"
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
- user-defined tools (MFC Extensions)
ms.assetid: cb887421-78ce-4652-bc67-96a53984ccaa
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 17f0751a2cb3f78730ec948d737dc99b85c2e735
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="user-defined-tools"></a>Narzędzia zdefiniowane przez użytkownika
MFC obsługuje narzędzia zdefiniowane przez użytkownika. Narzędzia zdefiniowane przez użytkownika jest polecenie specjalne, które wykonuje program zewnętrznych, określone przez użytkownika. Procesu dostosowywania służy do zarządzania narzędzia zdefiniowane przez użytkownika. Jednak nie można użyć tego procesu, jeśli obiekt aplikacji nie jest pochodną [CWinAppEx klasy](../mfc/reference/cwinappex-class.md). Aby uzyskać więcej informacji dotyczących dostosowywania, zobacz [Dostosowywanie MFC](../mfc/customization-for-mfc.md).  
  
 Jeśli włączona jest obsługa narzędzi zdefiniowane przez użytkownika, w oknie dialogowym dostosowywania automatycznie uwzględnia **narzędzia** kartę. Na poniższej ilustracji pokazano **narzędzia** strony.  
  
 ![Etykietka narzędzia w oknie dialogowym Dostosuj](../mfc/media/custdialogboxtoolstab.png "custdialogboxtoolstab")  
Karta narzędzi okna dialogowego dostosowania  
  
## <a name="enabling-user-defined-tools-support"></a>Włączenie użytkownika narzędzia pomocy technicznej  
 Aby włączyć narzędzia zdefiniowane przez użytkownika w aplikacji, należy wywołać [CWinAppEx::EnableUserTools](../mfc/reference/cwinappex-class.md#enableusertools). Jednak należy najpierw zdefiniować kilka stałych w plikach zasobów aplikacji w celu użycia jako parametry dla tego wywołania.  
  
 W edytorze zasobów należy utworzyć fikcyjny polecenia, które używa identyfikatora odpowiednie polecenie. W poniższym przykładzie używamy **ID_TOOLS_ENTRY** jako identyfikator polecenia. Ten identyfikator polecenia oznacza lokalizacji w menu, gdzie platformę powoduje wstawienie narzędzia zdefiniowane przez użytkownika.  
  
 Należy ustawić Odłóż niektórych kolejnych identyfikatorów w tabeli ciągów do reprezentowania narzędzia zdefiniowane przez użytkownika. Liczba parametrów, które wyznaczoną wynosi maksymalna liczba użytkowników narzędzia, które użytkownicy mogą definiować. W poniższym przykładzie są o nazwie **ID_USER_TOOL1** za pośrednictwem **ID_USER_TOOL10**.  
  
 Możesz również zaoferować sugestie użytkowników, aby ułatwić im wybierz katalogów i argumenty dla zewnętrznych programów, które będą wywoływane jako narzędzia. Aby to zrobić, należy utworzyć dwa menu podręcznego w edytorze zasobów. W poniższym przykładzie są one nazywane **IDR_MENU_ARGS** i **IDR_MENU_DIRS**. Dla każdego polecenia w menu należy zdefiniować ciąg w tabeli ciągów Twojej aplikacji. Identyfikator zasobu ciągu musi być taki sam identyfikator polecenia.  
  
 Można również utworzyć klasy pochodnej z [klasy CUserTool](../mfc/reference/cusertool-class.md) zastąpić domyślną implementację. Aby to zrobić, należy przekazać dane środowiska uruchomieniowego dla klasy pochodnej jako czwartego parametru w CWinAppEx::EnableUserTools zamiast runtime_class — ([CUserTool klasy](../mfc/reference/cusertool-class.md)).  
  
 Po zdefiniowaniu stałe odpowiednie wywołania [CWinAppEx::EnableUserTools](../mfc/reference/cwinappex-class.md#enableusertools) Aby włączyć narzędzia zdefiniowane przez użytkownika.  
  
 Następujące wywołanie metody przedstawia sposób użycia tych stałe:  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#1](../mfc/codesnippet/cpp/user-defined-tools_1.cpp)]  
  
 W tym przykładzie zostanie włączone na karcie Narzędzia **dostosowywania** okno dialogowe. Platformę spowoduje zastąpienie dowolnego polecenia, który jest zgodny z Identyfikatorem polecenia **ID_TOOLS_ENTRY** dowolnego menu przy użyciu zestawu narzędzi zdefiniowanych użytkownika przy każdym otwarciu tego menu. Identyfikatory poleceń **ID_USER_TOOL1** za pośrednictwem **ID_USER_TOOL10** są zarezerwowane do użytku dla narzędzia zdefiniowane przez użytkownika. Klasa [klasy CUserTool](../mfc/reference/cusertool-class.md) obsługuje wywołania do narzędzi użytkownika. Ustawienia na karcie Narzędzia **dostosowywania** okno dialogowe zawiera przyciski z prawej strony pola wejścia argumentu i katalog na dostęp do menu **IDR_MENU_ARGS** i **IDR_MENU_DIRS**. Platformę, gdy użytkownik wybierze polecenie w jednym z tych menu, dołącza do odpowiednim polu tekstowym, ciąg, który ma taki sam identyfikator polecenia. identyfikator zasobu  
  
### <a name="including-predefined-tools"></a>W tym narzędzia wstępnie zdefiniowane  
 Jeśli chcesz wstępnie niektóre narzędzia podczas uruchamiania aplikacji, konieczne jest przesłonięcie [CFrameWnd::LoadFrame](../mfc/reference/cframewnd-class.md#loadframe) metody okna głównego aplikacji. W tej metody należy wykonać następujące kroki.  
  
##### <a name="to-add-new-tools-in-loadframe"></a>Aby dodać nowe narzędzia LoadFrame  
  
1.  Wskaźnik do uzyskania [klasy CUserToolsManager](../mfc/reference/cusertoolsmanager-class.md) obiektu przez wywołanie metody [CWinAppEx::GetUserToolsManager](../mfc/reference/cwinappex-class.md#getusertoolsmanager).  
  
2.  Dla każdego narzędzia, który chcesz utworzyć, wywołaj [CUserToolsManager::CreateNewTool](../mfc/reference/cusertoolsmanager-class.md#createnewtool). Ta metoda zwraca wskaźnik do [klasy CUserTool](../mfc/reference/cusertool-class.md) obiektu i dodaje narzędzie nowo utworzonego użytkownika do wewnętrznej kolekcji narzędzia. Jeśli podane informacje środowiska uruchomieniowego dla klasy pochodnej [klasy CUserTool](../mfc/reference/cusertool-class.md) jako czwartego parametru [CWinAppEx::EnableUserTools](../mfc/reference/cwinappex-class.md#enableusertools), [CUserToolsManager::CreateNewTool](../mfc/reference/cusertoolsmanager-class.md#createnewtool) wystąpienia, a zamiast tego zwrócić wystąpienia tej klasy.  
  
3.  Dla każdego narzędzia ustawić jej etykieta tekstowa przez ustawienie `CUserTool::m_strLabel` i ustawiony przez wywołanie polecenia `CUserTool::SetCommand`. Domyślna implementacja [klasy CUserTool](../mfc/reference/cusertool-class.md) automatycznie pobiera dostępnych ikon z programu, które jest określone w wywołaniu `SetCommand`.  
  
## <a name="see-also"></a>Zobacz też  
 [Dostosowywanie na potrzeby MFC](../mfc/customization-for-mfc.md)   
 [Klasa CUserTool](../mfc/reference/cusertool-class.md)   
 [Klasa CUserToolsManager](../mfc/reference/cusertoolsmanager-class.md)   
 [Klasa CWinAppEx](../mfc/reference/cwinappex-class.md)




