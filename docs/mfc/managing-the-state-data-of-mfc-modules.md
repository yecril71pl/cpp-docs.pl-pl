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
ms.openlocfilehash: 64888b8ab53ebd80f328e1efe79df6256f30f9b6
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622573"
---
# <a name="managing-the-state-data-of-mfc-modules"></a>Zarządzanie danymi stanu modułów MFC

W tym artykule omówiono dane stanu modułów MFC i sposób aktualizowania tego stanu, gdy przepływ wykonywania (kod ścieżki jest wykonywany przez aplikację po jej uruchomieniu) wprowadza i opuszcza moduł. Omawiane są również przełączenie Stanów modułów przy użyciu AFX_MANAGE_STATE i METHOD_PROLOGUE makr.

> [!NOTE]
> Termin "moduł" odnosi się do programu wykonywalnego lub biblioteki DLL (lub zestawu bibliotek DLL), która działa niezależnie od reszty aplikacji, ale używa udostępnionej kopii biblioteki MFC DLL. Kontrolka ActiveX jest typowym przykładem modułu.

Jak pokazano na poniższej ilustracji, MFC zawiera dane stanu dla każdego modułu używanego w aplikacji. Przykłady tych danych obejmują uchwyty wystąpienia systemu Windows (używane do ładowania zasobów), wskaźniki do bieżących `CWinApp` i `CWinThread` obiektów aplikacji, liczby odwołań do modułu OLE oraz różne mapy, które utrzymują połączenia między dojściami do obiektów systemu Windows i odpowiednimi wystąpieniami obiektów MFC. Jeśli jednak aplikacja używa wielu modułów, dane stanu każdego modułu nie są szerokie dla aplikacji. Natomiast każdy moduł ma własną prywatną kopię danych stanu MFC.

![Dane stanu pojedynczego modułu &#40;aplikacji&#41;](../mfc/media/vc387n1.gif "Dane stanu pojedynczego modułu &#40;aplikacji&#41;") <br/>
Dane stanu pojedynczego modułu (aplikacji)

Dane stanu modułu są zawarte w strukturze i są zawsze dostępne za pośrednictwem wskaźnika do tej struktury. Gdy przepływ wykonywania przechodzi do określonego modułu, jak pokazano na poniższej ilustracji, stan tego modułu musi być stanem "bieżący" lub "obowiązuje". W związku z tym każdy obiekt wątku ma wskaźnik do efektywnej struktury stanu tej aplikacji. Aktualizowanie tego wskaźnika przez cały czas jest niezbędne do zarządzania stanem globalnym aplikacji i utrzymywania integralności stanu każdego modułu. Nieprawidłowe zarządzanie stanem globalnym może prowadzić do nieprzewidywalnego zachowania aplikacji.

![Dane stanu wielu modułów](../mfc/media/vc387n2.gif "Dane stanu wielu modułów") <br/>
Dane stanu wielu modułów

Innymi słowy każdy moduł jest odpowiedzialny za poprawne przełączanie między Stanami modułów we wszystkich punktach wejścia. "Punkt wejścia" jest dowolnym miejscem, w którym przepływ wykonywania może wprowadzać kod modułu. Punkty wejścia obejmują:

- [Funkcje eksportowane w bibliotece DLL](exported-dll-function-entry-points.md)

- [Funkcje składowe interfejsów COM](com-interface-entry-points.md)

- [Procedury okna](window-procedure-entry-points.md)

## <a name="see-also"></a>Zobacz też

[Tematy ogólne dotyczące MFC](general-mfc-topics.md)
