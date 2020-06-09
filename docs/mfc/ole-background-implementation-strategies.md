---
title: 'Podstawy OLE: strategie implementacji'
ms.date: 11/04/2016
helpviewer_keywords:
- OLE [MFC], development strategy
- OLE applications [MFC], implementing OLE
- applications [OLE], implementing OLE
ms.assetid: 0875ddae-99df-488c-82c6-164074a81058
ms.openlocfilehash: 90517f9b37872dd7de0ce1a2d08da94c93e6f8f8
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619903"
---
# <a name="ole-background-implementation-strategies"></a>Podstawy OLE: strategie implementacji

W zależności od aplikacji istnieją cztery możliwe strategie implementacji umożliwiające dodanie obsługi OLE:

- Piszesz nową aplikację.

   Ta sytuacja zwykle wymaga najmniejszej pracy. Uruchom Kreatora aplikacji MFC i wybierz opcję Zaawansowane funkcje lub Obsługa dokumentu złożonego, aby utworzyć aplikację szkieletową. Aby uzyskać informacje na temat tych opcji i ich działania, zobacz artykuł [Tworzenie programu MFC exe](reference/mfc-application-wizard.md).

- Masz program zapisany w biblioteka MFC w wersji 2,0 lub nowszej, która nie obsługuje OLE.

   Utwórz nową aplikację za pomocą Kreatora aplikacji MFC, jak wspomniano wcześniej, a następnie skopiuj i wklej kod z nowej aplikacji do istniejącej aplikacji. Będzie to działało w przypadku serwerów, kontenerów lub zautomatyzowanych aplikacji. Przykład tej strategii można znaleźć w przykładowym przykładzie [bazgrołów](../overview/visual-cpp-samples.md) MFC.

- Masz program biblioteka MFC, który implementuje obsługę OLE w wersji 1,0.

   Zapoznaj się z [uwagą technicznyą MFC 41](tn041-mfc-ole1-migration-to-mfc-ole-2.md) dla tej strategii konwersji.

- Masz aplikację, która nie została zapisywana przy użyciu Microsoft Foundation Classes i która może nie mieć zaimplementowanej obsługi OLE.

   Ta sytuacja wymaga najwięcej pracy. Jednym z rozwiązań jest utworzenie nowej aplikacji, jak w pierwszej strategii, a następnie skopiowanie i wklejenie istniejącego kodu do niego. Jeśli istniejący kod jest zapisywana w C, może być konieczne jego zmodyfikowanie, aby można było kompilować kod w języku C++. Jeśli kod C wywołuje interfejs API systemu Windows, nie trzeba go zmieniać, aby używać klas Microsoft Foundation. Takie podejście prawdopodobnie będzie wymagało pewnej restrukturyzacji programu, aby obsługiwała architekturę dokumentu/widoku używaną w wersjach 2,0 i wyższych Microsoft Foundation Classes. Aby uzyskać więcej informacji na temat tej architektury, zobacz [Uwagi techniczne 25](tn025-document-view-and-frame-creation.md).

Po ustaleniu strategii należy odczytać artykuły dotyczące [kontenerów](containers.md) lub [serwerów](servers.md) (w zależności od typu aplikacji) lub przejrzeć przykładowe programy lub oba te elementy. Przykłady MFC OLE [OCLIENT](../overview/visual-cpp-samples.md) i [HIERSVR](../overview/visual-cpp-samples.md) pokazują, jak zaimplementować odpowiednio różne aspekty kontenerów i serwerów. W różnych punktach w tych artykułach są określane pewne funkcje w tych przykładach jako przykłady omawianych technik.

## <a name="see-also"></a>Zobacz też

[Podstawy OLE](ole-background.md)<br/>
[Kontenery: implementowanie kontenera](containers-implementing-a-container.md)<br/>
[Serwery: implementowanie serwera](servers-implementing-a-server.md)<br/>
[Kreator aplikacji MFC](reference/mfc-application-wizard.md)
