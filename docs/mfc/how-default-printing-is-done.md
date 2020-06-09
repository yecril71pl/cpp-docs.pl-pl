---
title: Jak jest wykonywane drukowanie domyślne
ms.date: 11/04/2016
helpviewer_keywords:
- default printing
- printing [MFC], default
- defaults, printing
ms.assetid: 0f698459-0fc9-4d43-97da-29cf0f65daa2
ms.openlocfilehash: 9ca79ec69037b960e7c455f6ab8abd8833b9a8a0
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618586"
---
# <a name="how-default-printing-is-done"></a>Jak jest wykonywane drukowanie domyślne

W tym artykule wyjaśniono domyślny proces drukowania w systemie Windows pod kątem platformy MFC.

W aplikacjach MFC Klasa widoku ma funkcję członkowską o nazwie `OnDraw` , która zawiera cały kod rysowania. `OnDraw`Pobiera wskaźnik do obiektu [przechwytywania](reference/cdc-class.md) jako parametr. Ten `CDC` obiekt reprezentuje kontekst urządzenia do odbierania obrazu utworzonego przez program `OnDraw` . Gdy okno wyświetlania dokumentu otrzymuje komunikat [WM_PAINT](/windows/win32/gdi/wm-paint) , struktura wywołuje `OnDraw` i przekazuje do niego kontekst urządzenia dla ekranu (obiekt [CPaintDC](reference/cpaintdc-class.md) , aby był określony). W związku z tym `OnDraw` dane wyjściowe trafiają do ekranu.

W programowaniu dla systemu Windows wysyłanie danych wyjściowych do drukarki jest bardzo podobne do wysyłania danych wyjściowych do ekranu. Wynika to z faktu, że interfejs urządzenia graficznego (GDI) systemu Windows jest niezależny od sprzętu. Możesz użyć tych samych funkcji GDI do wyświetlania ekranu lub do drukowania po prostu przy użyciu odpowiedniego kontekstu urządzenia. Jeśli `CDC` `OnDraw` otrzymany obiekt reprezentuje drukarkę, `OnDraw` dane wyjściowe trafiają do drukarki.

W tym artykule wyjaśniono, jak aplikacje MFC mogą wykonywać proste drukowanie, bez konieczności dodatkowego wysiłku. Struktura zajmuje się wyświetleniem okna dialogowego drukowanie i utworzeniem kontekstu urządzenia dla drukarki. Gdy użytkownik wybierze polecenie Drukuj z menu plik, widok przekaże ten kontekst urządzenia do programu `OnDraw` , co spowoduje narysowanie dokumentu na drukarce.

Istnieją jednak pewne znaczące różnice między drukowaniem i wyświetlaniem ekranu. Podczas drukowania należy podzielić dokument na osobne strony i wyświetlić je pojedynczo, zamiast wyświetlać część, która jest widoczna w oknie. Jako współrzuty trzeba mieć świadomość rozmiaru papieru (rozmiaru litery, rozmiaru prawnego lub koperty)... Możesz chcieć drukować w różnych orientacjach, takich jak orientacja pozioma lub pionowa. Biblioteka MFC nie może przewidzieć, w jaki sposób aplikacja będzie obsługiwać te problemy, dzięki czemu umożliwia dodanie tych funkcji.

Ten protokół jest opisany w [dokumentacji wielostronicowej](multipage-documents.md)artykułu.

## <a name="see-also"></a>Zobacz też

[Drukowanie](printing.md)
