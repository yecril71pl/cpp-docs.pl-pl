---
title: 'Podstawy OLE: Strategie implementacji'
ms.date: 11/04/2016
helpviewer_keywords:
- OLE [MFC], development strategy
- OLE applications [MFC], implementing OLE
- applications [OLE], implementing OLE
ms.assetid: 0875ddae-99df-488c-82c6-164074a81058
ms.openlocfilehash: 83a1089ecaaaa9bd0dd1d928cd3d1869e5017a4a
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58774389"
---
# <a name="ole-background-implementation-strategies"></a>Podstawy OLE: Strategie implementacji

W zależności od aplikacji dostępne są cztery strategie możliwą implementację dodanie obsługi:

- Podczas pisania nowych aplikacji.

   Taka sytuacja jest zazwyczaj wymaga najmniejszej pracy. Uruchom Kreatora aplikacji MFC i wybierz pozycję Funkcje zaawansowane lub Obsługa dokumentów złożonych, aby utworzyć szkielet aplikacji. Aby uzyskać informacje na temat tych opcji i co zrobić, zobacz artykuł [tworzenie MFC EXE programu](../mfc/reference/mfc-application-wizard.md).

- Masz program napisany w języku bibliotekę Microsoft Foundation Class wersja 2.0 lub nowszej, który nie obsługuje OLE.

   Utwórz nową aplikację za pomocą Kreatora aplikacji MFC, jak wcześniej wspomniano, a następnie skopiuj i Wklej kod z nową aplikację do istniejącej aplikacji. Będzie on działać w przypadku serwerów, kontenerów lub zautomatyzowane aplikacji. Zobacz MFC [BAZGROŁY](../overview/visual-cpp-samples.md) przykładowe przykładem tej strategii.

- Masz program bibliotekę Microsoft Foundation Class, który implementuje obsługi wersji 1.0.

   Zobacz [MFC techniczne Uwaga 41](../mfc/tn041-mfc-ole1-migration-to-mfc-ole-2.md) tej strategii konwersji.

- Gdy masz już aplikację, który nie został zapisany przy użyciu Microsoft Foundation Classes i które mogą lub nie zostały zaimplementowane Obsługa OLE.

   Taka sytuacja wymaga najwięcej pracy. Jedno z podejść jest tworzenie nowej aplikacji, jak pierwsza strategia, a następnie skopiuj i Wklej istniejący kod. Jeśli istniejący kod jest napisany w języku C, może być konieczne zmiany, dzięki czemu można kompilować jako kod C++. Jeśli kod C wywołuje interfejs API Windows, nie trzeba zmienić go do użycia klasy Microsoft Foundation. Takie podejście, prawdopodobnie będzie wymagać niektóre restrukturyzacji programu do obsługi architektury dokument/widok posługują się w wersji 2.0 lub nowszej klasy Microsoft Foundation. Aby uzyskać więcej informacji na temat tej architektury, zobacz [techniczne 25 Uwaga](../mfc/tn025-document-view-and-frame-creation.md).

Po określeniu strategii, powinny albo odczytu [kontenery](../mfc/containers.md) lub [serwerów](../mfc/servers.md) artykuły (w zależności od typu aplikacji pisania), lub przejrzyj przykładowe programy i / lub. Przykłady MFC OLE [OCLIENT](../overview/visual-cpp-samples.md) i [HIERSVR](../overview/visual-cpp-samples.md) pokazują sposób implementacji różnych aspektów kontenery i serwery, odpowiednio. W różnych punktach tych artykułów będzie odnosić się niektórych funkcji w tych przykładach jako przykładów, techniki omawiana.

## <a name="see-also"></a>Zobacz także

[Podstawy OLE](../mfc/ole-background.md)<br/>
[Kontenery: Implementowanie kontenera](../mfc/containers-implementing-a-container.md)<br/>
[Serwery: Implementowanie serwera](../mfc/servers-implementing-a-server.md)<br/>
[Kreator aplikacji MFC](../mfc/reference/mfc-application-wizard.md)
