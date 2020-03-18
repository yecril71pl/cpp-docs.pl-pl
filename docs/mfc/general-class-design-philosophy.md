---
title: Ogólne zasady projektowania klas
ms.date: 11/04/2016
helpviewer_keywords:
- designing classes [MFC]
- MFC, Windows API
- Visual C, Windows API calls
- classes [MFC], MFC class design
- Windows API [MFC], and MFC
ms.assetid: e6861ae0-1581-4d9c-9ddf-63f9afcdb913
ms.openlocfilehash: 34a173802e3fa43615c05da4ce747592f851228f
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79441189"
---
# <a name="general-class-design-philosophy"></a>Ogólne zasady projektowania klas

System Microsoft Windows został zaprojektowany długo, C++ zanim język stał się popularny. Ze względu na to, że tysiące aplikacji korzysta z interfejsu programowania aplikacji systemu Windows (API) dla języka C, ten interfejs będzie obsługiwany w przyszłości. W C++ związku z tym każdy interfejs systemu Windows musi być zbudowany w oparciu o interfejs API języka C. Gwarantuje to, C++ że aplikacje będą mogły współistnieć z aplikacjami języka C.

Biblioteka MFC to interfejs zorientowany obiektowo dla systemu Windows, który spełnia następujące cele projektowe:

- Znacząca redukcja nakładu pracy w celu napisania aplikacji dla systemu Windows.

- Szybkość wykonywania porównywalna z tym interfejsem API języka C.

- Minimalny koszt rozmiaru kodu.

- Możliwość bezpośredniej wywołania dowolnej funkcji systemu Windows C.

- Łatwiejsza Konwersja istniejących aplikacji C do C++programu.

- Możliwość wykorzystania z istniejącej podstawy środowiska programowania systemu Windows w języku C.

- Łatwiejsze korzystanie z interfejsu API systemu Windows C++ za pomocą języka C.

- Łatwiejsze w użyciu jeszcze zaawansowane abstrakcje skomplikowanych funkcji, takich jak kontrolki ActiveX, obsługa bazy danych, drukowanie, paski narzędzi i paski stanu.

- Prawdziwy interfejs API systemu C++ Windows, aby C++ efektywnie korzystać z funkcji języka.

Aby uzyskać więcej informacji na temat projektowania biblioteki MFC, zobacz:

- [Struktura aplikacji](../mfc/application-framework.md)

- [Relacja z interfejsem API języka C](../mfc/relationship-to-the-c-language-api.md)

## <a name="see-also"></a>Zobacz też

[Przegląd klas](../mfc/class-library-overview.md)
