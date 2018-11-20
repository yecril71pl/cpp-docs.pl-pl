---
title: Zarządzanie danymi stanu modułów MFC
ms.date: 11/19/2018
helpviewer_keywords:
- global state [MFC]
- data management [MFC], MFC modules
- window procedure entry points [MFC]
- exported interfaces and global state [MFC]
- module states [MFC], saving and restoring
- data management [MFC]
- MFC, managing state data
- multiple modules [MFC]
- module state restored [MFC]
ms.assetid: 81889c11-0101-4a66-ab3c-f81cf199e1bb
ms.openlocfilehash: d1bed6f3b0dddf0d4ae5e8309d683e52c9e82410
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/20/2018
ms.locfileid: "52174891"
---
# <a name="managing-the-state-data-of-mfc-modules"></a>Zarządzanie danymi stanu modułów MFC

W tym artykule omówiono dane stanu modułów MFC i jak ten stan jest aktualizowany po przepływem wykonania (kod ścieżki trwa przy użyciu aplikacji podczas wykonywania) wprowadza i pozostawia modułu. Przełączanie Stany modułu za pomocą makra AFX_MANAGE_STATE i METHOD_PROLOGUE jest również omówiona.

> [!NOTE]
>  Termin "module" w tym miejscu odnosi się program wykonywalny lub biblioteka DLL (lub zestaw bibliotek DLL), które będą działać niezależnie od pozostałej części aplikacji, ale używa udostępnionego kopię biblioteki MFC DLL. Kontrolki ActiveX jest typowym przykładem modułu.

Jak pokazano na poniższej ilustracji, MFC posiada dane o stanie dla każdego modułu, używane w aplikacji. Dane te przykłady uchwytów wystąpienia Windows (używane do ładowania zasobów), wskaźniki do bieżącego `CWinApp` i `CWinThread` obiekty aplikacji, liczbę odwołań modułu OLE i różnych map, zapewniające połączeń między Windows obiekt dojścia i odpowiednie wystąpienia obiektów MFC. Gdy aplikacja używa wiele modułów, dane o stanie każdego modułu, nie jest jednak aplikacji szerokości. Przeciwnie każdy moduł ma własną prywatną kopię danych o stanie biblioteki MFC.

![Stan danych pojedynczym module &#40;aplikacji&#41;](../mfc/media/vc387n1.gif "danych pojedynczy moduł o stanie &#40;aplikacji&#41;") <br/>
Danych o stanie jednego modułu (aplikacja)

Dane o stanie modułu jest zawarta w strukturze i jest zawsze dostępna za pośrednictwem wskaźnik do tej struktury. Gdy przepływem wykonania wprowadza danego modułu, jak pokazano na poniższej ilustracji, ten moduł stan musi mieć stan "bieżącej" lub "od". W związku z tym każdy obiekt wątku zawiera wskaźnik do struktury skuteczne stan tej aplikacji. Utrzymywanie ten wskaźnik, ciągle razy jest zachowywana jest integralność stanu każdego modułu i zarządzanie nimi globalny stan aplikacji. Zarządzanie niepoprawny stan globalny może spowodować nieprzewidywalne zachowanie aplikacji.

![Stan danych wiele modułów](../mfc/media/vc387n2.gif "danych wiele modułów o stanie") <br/>
Danymi stanu modułów wielu

Innymi słowy każdy moduł jest odpowiedzialny za poprawnie przełączania się między Stany modułu we wszystkich punktów wejścia. "Punkt wejścia" jest dowolnym miejscu, w którym przepływem wykonania można wprowadzić kod modułu. Punkty wejścia obejmują:

- [Eksportowanych funkcji w bibliotece DLL](../mfc/exported-dll-function-entry-points.md)

- [Funkcje składowe typów interfejsów COM](../mfc/com-interface-entry-points.md)

- [Procedury okna](../mfc/window-procedure-entry-points.md)

## <a name="see-also"></a>Zobacz też

[Tematy ogólne dotyczące MFC](../mfc/general-mfc-topics.md)
