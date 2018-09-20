---
title: Opieranie się na strukturze | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- application-specific classes [MFC]
- application framework [MFC], building applications
- applications [MFC]
- MFC, application development
ms.assetid: 883f0f19-866f-4221-8a3d-5607941dc8d0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4ca0ebd9bf03df8725c14df8d2aca1f7858b7b65
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46396184"
---
# <a name="building-on-the-framework"></a>Opieranie się na strukturze

Twoja rola w Konfigurowanie aplikacji za pomocą programu MFC framework jest podać kod źródłowy specyficzne dla aplikacji i łączenia składników przez określenie, jakie komunikaty i polecenia, do których ta osoba odpowie. Używasz języka C++ i standardowych technik C++ dziedziczyć dostarczane przez bibliotekę klas własnych klas specyficznych dla aplikacji, a także Przesłoń i rozszerzyć zachowanie klasy bazowej.

W tematach pokrewnych w poniższych tabelach opisano ogólną sekwencją operacje, które zwykle wykonują i Twoich obowiązkach i obowiązki w ramach:

- [Tworzenie aplikacji z architekturą sekwencji](../mfc/sequence-of-operations-for-building-mfc-applications.md)

- [Sekwencja operacji przy tworzeniu aplikacji OLE](../mfc/sequence-of-operations-for-creating-ole-applications.md)

- [Sekwencja operacji przy tworzeniu kontrolek ActiveX](../mfc/sequence-of-operations-for-creating-activex-controls.md)

- [Sekwencja operacji przy tworzeniu aplikacji bazy danych](../mfc/sequence-of-operations-for-creating-database-applications.md)

W większości przypadków możesz wykonać te tabele jako sekwencja procedury służące do tworzenia aplikacji MFC, mimo że niektóre kroki są alternatywne rozwiązania. Na przykład większość aplikacji używa jeden typ widoku klasy z kilku dostępnych typów.

## <a name="see-also"></a>Zobacz też

[Tematy ogólne dotyczące MFC](../mfc/general-mfc-topics.md)

