---
title: Inicjowanie i oczyszczanie dokumentów i widoków
ms.date: 11/04/2016
helpviewer_keywords:
- initializing documents [MFC]
- views [MFC], cleaning up
- documents [MFC], initializing
- documents [MFC], cleaning up
- views [MFC], initializing
- initializing objects [MFC], document objects
- document objects [MFC], life cycle of
- initializing views [MFC]
ms.assetid: 95d6f09b-a047-4079-856a-ae7d0548e9d2
ms.openlocfilehash: c5beed5618d4fa991160ad1688a5a686aeaa842f
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626368"
---
# <a name="initializing-and-cleaning-up-documents-and-views"></a>Inicjowanie i oczyszczanie dokumentów i widoków

Poniżej przedstawiono wskazówki dotyczące inicjowania i czyszczenia danych po dokumentach i widokach:

- Struktura MFC inicjuje dokumenty i widoki; wszystkie dodawane do nich dane są inicjowane.

- Struktura czyści dokumenty i widoki blisko; musisz cofnąć alokację pamięci przydzieloną na stercie z poziomu funkcji składowych tych dokumentów i widoków.

> [!NOTE]
> Należy odwołać to inicjowanie dla całej aplikacji najlepiej wykonać w przesłonięciu funkcji składowej [InitInstance](reference/cwinapp-class.md#initinstance) klasy `CWinApp` , a czyszczenie dla całej aplikacji jest najlepszym rozwiązaniem w przesłonięciu `CWinApp` funkcji składowej [ExitInstance](reference/cwinapp-class.md#exitinstance).

Cykl życia dokumentu (i jego okna i widok ramki oraz widoku) w aplikacji MDI jest następujący:

1. Podczas tworzenia dynamicznego Konstruktor dokumentu jest wywoływany.

1. Dla każdego nowego dokumentu wywoływana jest [OnNewDocument](reference/cdocument-class.md#onnewdocument) lub [OnOpenDocument](reference/cdocument-class.md#onopendocument) dokumentu.

1. Użytkownik współdziała z dokumentem przez cały okres istnienia. Zazwyczaj dzieje się tak, gdy użytkownik pracuje nad danymi dokumentu w widoku, wybierając i edytując dane. Widok przekazuje zmiany do dokumentu w celu przechowywania i aktualizowania innych widoków. W tym czasie zarówno dokument, jak i widok mogą obsługiwać polecenia.

1. Struktura wywołuje [DeleteContents](reference/cdocument-class.md#deletecontents) do usuwania danych specyficznych dla dokumentu.

1. Wywołano destruktor dokumentu.

W aplikacji SDI krok 1 jest wykonywany raz, podczas pierwszego tworzenia dokumentu. Następnie kroki od 2 do 4 są wykonywane wielokrotnie przy każdym otwarciu nowego dokumentu. Nowy dokument używa ponownie istniejącego obiektu dokumentu. Na koniec krok 5 jest wykonywany po zakończeniu aplikacji.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o

- [Inicjowanie dokumentów i widoków](initializing-documents-and-views.md)

- [Oczyszczanie dokumentów i widoków](cleaning-up-documents-and-views.md)

## <a name="see-also"></a>Zobacz też

[Architektura dokumentu/widoku](document-view-architecture.md)
