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
ms.openlocfilehash: c8e79f54ed586201a7d82327662643a9a241b8f4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81357266"
---
# <a name="managing-the-state-data-of-mfc-modules"></a>Zarządzanie danymi stanu modułów MFC

W tym artykule omówiono dane o stanie modułów MFC i jak ten stan jest aktualizowany, gdy przepływ wykonywania (kod ścieżki przechodzi przez aplikację podczas wykonywania) wchodzi i pozostawia moduł. Omówiono również stany modułów przełączania z makrami AFX_MANAGE_STATE i METHOD_PROLOGUE.

> [!NOTE]
> Termin "moduł" w tym miejscu odnosi się do programu wykonywalnego lub biblioteki DLL (lub zestaw bibliotek DLL), które działają niezależnie od reszty aplikacji, ale używa udostępnionej kopii biblioteki DLL MFC. Formant ActiveX jest typowym przykładem modułu.

Jak pokazano na poniższym rysunku, MFC ma dane o stanie dla każdego modułu używanego w aplikacji. Przykłady tych danych obejmują dojścia wystąpienia systemu Windows (używane do ładowania zasobów), wskaźniki do bieżącej `CWinApp` i `CWinThread` obiektów aplikacji, liczby odwołań modułu OLE i różnych map, które obsługują połączenia między uchwytami obiektów systemu Windows i odpowiadającymi im wystąpieniami obiektów MFC. Jednak gdy aplikacja używa wielu modułów, dane o stanie każdego modułu nie jest szeroki zakres aplikacji. Zamiast tego każdy moduł ma własną kopię prywatną danych o stanie MFC.

![Dane o stanie pojedynczego modułu &#40;&#41;aplikacji](../mfc/media/vc387n1.gif "Dane o stanie pojedynczego modułu &#40;&#41; aplikacji") <br/>
Dane o stanie pojedynczego modułu (aplikacji)

Dane o stanie modułu są zawarte w strukturze i są zawsze dostępne za pośrednictwem wskaźnika do tej struktury. Gdy przepływ wykonania wchodzi do określonego modułu, jak pokazano na poniższej ilustracji, stan tego modułu musi być stanem "bieżącym" lub "skutecznym". W związku z tym każdy obiekt wątku ma wskaźnik do efektywnej struktury stanu tej aplikacji. Aktualizowanie tego wskaźnika przez cały czas ma zasadnicze znaczenie dla zarządzania stanem globalnym aplikacji i zachowania integralności stanu każdego modułu. Nieprawidłowe zarządzanie stanem globalnym może prowadzić do nieprzewidywalnego zachowania aplikacji.

![Dane o stanie wielu modułów](../mfc/media/vc387n2.gif "Dane o stanie wielu modułów") <br/>
Dane o stanie wielu modułów

Innymi słowy, każdy moduł jest odpowiedzialny za poprawne przełączanie między stanami modułu we wszystkich jego punktach wejścia. "Punkt wejścia" to dowolne miejsce, w którym przepływ wykonania może wprowadzić kod modułu. Punkty wejścia obejmują:

- [Eksportowane funkcje w biblioteki DLL](../mfc/exported-dll-function-entry-points.md)

- [Funkcje członkowskie interfejsów COM](../mfc/com-interface-entry-points.md)

- [Procedury okienne](../mfc/window-procedure-entry-points.md)

## <a name="see-also"></a>Zobacz też

[Tematy ogólne dotyczące MFC](../mfc/general-mfc-topics.md)
