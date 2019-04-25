---
title: Ogólne zasady projektowania klas
ms.date: 11/04/2016
f1_keywords:
- vc.classes.mfc
helpviewer_keywords:
- designing classes [MFC]
- MFC, Windows API
- Visual C, Windows API calls
- classes [MFC], MFC class design
- Windows API [MFC], and MFC
ms.assetid: e6861ae0-1581-4d9c-9ddf-63f9afcdb913
ms.openlocfilehash: 4dfa11c73703f5f2d3d17f8278610d32178af679
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62219622"
---
# <a name="general-class-design-philosophy"></a>Ogólne zasady projektowania klas

Program Microsoft Windows została tak przygotowana, czas, zanim się języka C++. Tysiące aplikacji używają interfejsu programowania aplikacji (API) Windows języka C, ten interfejs zostanie zachowana w najbliższej przyszłości. Dowolny interfejs Windows C++ w związku z tym musi być utworzonych na szczycie procedurach interfejsu API języka C. Gwarantuje to, że aplikacji w języku C++ będzie pod kątem współistnienia z aplikacji C.

Biblioteki klas Microsoft Foundation jest zorientowany obiektowo interfejs Windows, która spełnia następujące cele projektu:

- Znaczne zmniejszenie wysiłku, aby napisać aplikację dla Windows.

- Szybkość wykonywania porównywalne z interfejsem API języka C.

- Kod minimalny rozmiar koszty.

- Możliwość bezpośrednio wywoływać żadnych funkcji Windows C.

- Łatwiejsze konwersji istniejących aplikacji C do języka C++.

- Możliwość się, jak korzystać z istniejących podstawy języka C Windows środowisko programowania.

- Łatwiejsze korzystanie z interfejsu API Windows przy użyciu języka C++ niż przy użyciu C.

- Łatwiejsze do użycia, ale zaawansowanych abstrakcje skomplikowane funkcji, takich jak kontrolki ActiveX, obsługa bazy danych, drukowanie, paski narzędzi i pasków stanu.

- Wartość true, interfejs API Windows dla języka C++, które skutecznie korzysta z funkcji języka C++.

Aby uzyskać więcej informacji o projektu biblioteki MFC zobacz:

- [Struktura aplikacji](../mfc/application-framework.md)

- [Relacja z interfejsem API języka C](../mfc/relationship-to-the-c-language-api.md)

## <a name="see-also"></a>Zobacz także

[Klasa — Przegląd](../mfc/class-library-overview.md)
