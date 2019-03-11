---
title: Pliki zasobów (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- resource files
- resources [C++]
- file types [C++], resource files
ms.assetid: 338a4a0f-0c62-4ef1-a34f-5d86262d93a4
ms.openlocfilehash: e19ad88a52467cd7ad2d5fa17dd964fd1bb38429
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/11/2019
ms.locfileid: "57747050"
---
# <a name="resource-files-c"></a>Pliki zasobów (C++)

Zasoby są elementy interfejsu, które zawierają informacje do użytkownika. Mapy bitowe, ikony, paski narzędzi i kursory są wszystkie zasoby. Niektóre zasoby mogą być zmieniane do wykonania akcji, takie jak wybór z menu lub wprowadzanie danych w oknie dialogowym.

Zobacz [pracy z zasobami](../windows/working-with-resource-files.md) Aby uzyskać więcej informacji.

|Nazwa pliku|Lokalizacja katalogu|Lokalizacja Eksploratora rozwiązań|Opis|
|---------------|------------------------|--------------------------------|-----------------|
|*Projname*.rc|*Projname*|Pliki źródłowe|Plik skryptu zasobu dla projektu. Plik skryptu zasobu zawiera następujące polecenie, w zależności od typu projektu i pomocy technicznej, wybrany dla projektu (na przykład, paski narzędzi, okna dialogowe lub HTML):<br /><br />-Definicja menu default.<br />— Tabele akceleratora i ciąg.<br />-Domyślnie **o** okno dialogowe.<br />-Innych oknach dialogowych.<br />-Plik ikony (res\\*Projname*.ico).<br />— Informacje o wersji.<br />-Map bitowych.<br />— Pasek narzędzi.<br />— Pliki HTML.<br /><br /> Plik zasobów zawiera standardowe zasoby MFC w pliku Afxres.rc pliku.|
|Resource.h|*Projname*|Pliki nagłówkowe|Plik nagłówka zasobów zawiera definicje dla zasobów używanych przez projekt.|
|*Projname*.rc2|*Projname*\res|Pliki źródłowe|Plik skryptu zawierający dodatkowe zasoby używane przez projekt. Można dołączyć plik .rc2 w pliku .rc projektu.<br /><br /> Plik .rc2 przydaje się, w tym zasoby używane przez kilka różnych projektach. Nie trzeba tworzyć te same zasoby dla różnych projektów, można umieścić je w pliku .rc2 i dołączyć plik .rc2 w pliku .rc głównego.|
|*Projname*.def|*Projname*|Pliki źródłowe|Plik definicji modułu projektu DLL. W przypadku formantu zawiera nazwę i opis kontrolki, a także rozmiar sterty środowiska wykonawczego.|
|*Projname*.ico|*Projname*\res|Pliki zasobów|Plik ikony dla projektu lub sterowania. Ikona ta pojawia się, gdy aplikacja jest zminimalizowana. Jest również używany w aplikacji **o** pole. Domyślnie biblioteka MFC zawiera ikonę MFC i ATL zawiera ikonę ATL.|
|*Projname*Doc.ico|*Projname*\res|Pliki zasobów|Plik ikony dla projektu MFC, który zawiera obsługę architektury dokumentu/widoku.|
|Toolbar.bmp|*Projname*\res|Pliki zasobów|Plik mapy bitowej reprezentujący aplikacja lub formant paska narzędzi lub palety. Ta mapa bitowa znajduje się w pliku zasobów projektu. Początkowy pasek narzędzi i pasek stanu, które są konstruowane w **cmainframe —** klasy.|
|ribbon.mfcribbon-ms|*Projname*\res|Pliki zasobów|Plik zasobu, który zawiera kod XML, który definiuje przyciskami, formanty i atrybuty na Wstążce. Aby uzyskać więcej informacji, zobacz [Projektant wstążki (MFC)](../mfc/ribbon-designer-mfc.md).|

## <a name="see-also"></a>Zobacz także

[Typy plików utworzonych dla projektów Visual C++](../ide/file-types-created-for-visual-cpp-projects.md)
