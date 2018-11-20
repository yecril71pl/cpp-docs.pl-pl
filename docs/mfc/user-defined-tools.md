---
title: Narzędzia zdefiniowane przez użytkownika
ms.date: 11/19/2018
helpviewer_keywords:
- user-defined tools (MFC Extensions)
ms.assetid: cb887421-78ce-4652-bc67-96a53984ccaa
ms.openlocfilehash: df8ba98fa1986052bae82b2afbdf40725298bef7
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/20/2018
ms.locfileid: "52175733"
---
# <a name="user-defined-tools"></a>Narzędzia zdefiniowane przez użytkownika

Biblioteka MFC obsługuje narzędzia zdefiniowane przez użytkownika. Narzędzia zdefiniowane przez użytkownika jest specjalnych poleceń, które wykonuje program zewnętrznych, określonych przez użytkownika. Proces dostosowywania służy do zarządzania narzędzia zdefiniowane przez użytkownika. Jednak nie można używać tego procesu, jeśli obiekt aplikacji nie pochodzi od [klasa CWinAppEx](../mfc/reference/cwinappex-class.md). Aby uzyskać więcej informacji na temat dostosowywania, zobacz [Dostosowywanie na potrzeby MFC](../mfc/customization-for-mfc.md).

Jeśli włączona jest obsługa narzędzi zdefiniowane przez użytkownika, w oknie dialogowym dostosowywania automatycznie uwzględnia **narzędzia** kartę. Poniższa ilustracja przedstawia **narzędzia** strony.

![Narzędzia karty w oknie dialogowym Dostosuj](../mfc/media/custdialogboxtoolstab.png "narzędzia karta w oknie dialogowym Dostosuj") <br/>
Karta narzędzia okna dialogowego Dostosowywanie

## <a name="enabling-user-defined-tools-support"></a>Włączanie użytkownika narzędzia pomocy technicznej

Aby włączyć narzędzia zdefiniowane przez użytkownika w aplikacji, należy wywołać [CWinAppEx::EnableUserTools](../mfc/reference/cwinappex-class.md#enableusertools). Jednakże należy najpierw zdefiniować kilka stałych w plikach zasobów aplikacji do użycia jako parametry dla tego wywołania.

W edytorze zasobów Utwórz zastępczy polecenia, które używa identyfikatora odpowiednie polecenie. W poniższym przykładzie użyto `ID_TOOLS_ENTRY` jako identyfikator polecenia. Ten identyfikator polecenia oznacza lokalizację w jednym lub kilku menu, gdy struktura wstawi narzędzia zdefiniowane przez użytkownika.

Należy ustawić na bok kilka kolejnych identyfikatorów w tabeli ciągów do reprezentowania narzędzia zdefiniowane przez użytkownika. Liczba ciągów, które należy zarezerwować jest równa maksymalnej liczbie narzędzi użytkownika, które użytkownicy mogą definiować. W poniższym przykładzie są one nazywane `ID_USER_TOOL1` za pośrednictwem `ID_USER_TOOL10`.

Sugestie można zaoferować użytkownikom, aby pomóc im Wybierz katalogi i argumenty dla zewnętrznych programów, które będą wywoływane jako narzędzia. Aby to zrobić, należy utworzyć dwa menu podręczne w edytorze zasobów. W poniższym przykładzie są one nazywane `IDR_MENU_ARGS` i `IDR_MENU_DIRS`. Dla każdego polecenia w menu należy zdefiniować ciąg w tabeli ciągów aplikacji. Identyfikator zasobu ciągu musi być taki sam identyfikator polecenia.

Można również tworzyć klasy pochodnej od [klasa CUserTool](../mfc/reference/cusertool-class.md) zastąpić domyślną implementację. Aby to zrobić, należy przekazać informacje środowiska uruchomieniowego dla klasy pochodnej jako czwarty parametr w CWinAppEx::EnableUserTools zamiast RUNTIME_CLASS ([klasa CUserTool](../mfc/reference/cusertool-class.md)).

Po zdefiniowaniu odpowiednie stałe, należy wywołać [CWinAppEx::EnableUserTools](../mfc/reference/cwinappex-class.md#enableusertools) umożliwiające narzędzia zdefiniowane przez użytkownika.

Poniższe wywołanie metody przedstawia sposób użycia tych stałe:

[!code-cpp[NVC_MFC_VisualStudioDemo#1](../mfc/codesnippet/cpp/user-defined-tools_1.cpp)]

W tym przykładzie jest uwzględniane na karcie Narzędzia **dostosowywania** okno dialogowe. Struktura spowoduje zastąpienie dowolnego polecenia, który jest zgodny z Identyfikatorem polecenia `ID_TOOLS_ENTRY` dowolnego menu za pomocą zestawu narzędzi użytkownika aktualnie zdefiniowanych w każdym przypadku, gdy użytkownik otwiera menu. Identyfikatory poleceń `ID_USER_TOOL1` za pośrednictwem `ID_USER_TOOL10` są zarezerwowane do użytku dla narzędzia zdefiniowane przez użytkownika. Klasa [klasa CUserTool](../mfc/reference/cusertool-class.md) obsługuje wywołania do narzędzi użytkownika. Na karcie Narzędzia **dostosowywania** okno dialogowe zawiera przyciski po prawej stronie pola wprowadzania argumentu i katalog na dostęp do menu **IDR_MENU_ARGS** i **IDR_MENU_DIRS**. Gdy użytkownik wybierze polecenie z jednego z tych menu, platformę dołącza do pola tekstowego odpowiedni ciąg, który ma identyfikator zasobu równa identyfikator polecenia.

### <a name="including-predefined-tools"></a>W tym narzędzia wstępnie zdefiniowane

Jeśli chcesz wstępnie niektóre narzędzia podczas uruchamiania aplikacji, konieczne jest przesłonięcie [CFrameWnd::LoadFrame](../mfc/reference/cframewnd-class.md#loadframe) metoda okna głównego aplikacji. W przypadku tej metody należy wykonać następujące czynności.

##### <a name="to-add-new-tools-in-loadframe"></a>Aby dodać nowe narzędzia w loadframe —

1. Uzyskiwanie wskaźnika do [klasa CUserToolsManager](../mfc/reference/cusertoolsmanager-class.md) obiektu przez wywołanie metody [CWinAppEx::GetUserToolsManager](../mfc/reference/cwinappex-class.md#getusertoolsmanager).

1. Każdego narzędzia, który ma zostać utworzona, należy wywołać [CUserToolsManager::CreateNewTool](../mfc/reference/cusertoolsmanager-class.md#createnewtool). Ta metoda zwraca wskaźnik do [klasa CUserTool](../mfc/reference/cusertool-class.md) obiektu i dodaje narzędzie nowo utworzone przez użytkownika do wewnętrznego zestaw narzędzi. Jeśli podane informacje środowiska uruchomieniowego dla klasy pochodnej [klasa CUserTool](../mfc/reference/cusertool-class.md) jako czwarty parametr [CWinAppEx::EnableUserTools](../mfc/reference/cwinappex-class.md#enableusertools), [CUserToolsManager::CreateNewTool](../mfc/reference/cusertoolsmanager-class.md#createnewtool) będzie wystąpienia i zamiast tego Zwraca wystąpienie tej klasy.

1. Dla każdego z tych narzędzi należy ustawić jej etykietę tekstową, ustawiając `CUserTool::m_strLabel` i ustaw jego polecenia przez wywołanie metody `CUserTool::SetCommand`. Domyślna implementacja klasy [klasa CUserTool](../mfc/reference/cusertool-class.md) automatycznie pobiera dostępna ikon z programu, który jest określony w wywołaniu `SetCommand`.

## <a name="see-also"></a>Zobacz też

[Dostosowywanie na potrzeby MFC](../mfc/customization-for-mfc.md)<br/>
[Klasa CUserTool](../mfc/reference/cusertool-class.md)<br/>
[Klasa CUserToolsManager](../mfc/reference/cusertoolsmanager-class.md)<br/>
[Klasa CWinAppEx](../mfc/reference/cwinappex-class.md)
