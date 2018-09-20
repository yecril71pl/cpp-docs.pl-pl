---
title: Zasady ogólne projektowania klas | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.mfc
dev_langs:
- C++
helpviewer_keywords:
- designing classes [MFC]
- MFC, Windows API
- Visual C, Windows API calls
- classes [MFC], MFC class design
- Windows API [MFC], and MFC
ms.assetid: e6861ae0-1581-4d9c-9ddf-63f9afcdb913
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8fe64ee4d9e6fc678d97c3e9fe37a85e53807541
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46416646"
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

## <a name="see-also"></a>Zobacz też

[Klasa — Przegląd](../mfc/class-library-overview.md)

