---
title: Pliki zasobów (C++)
ms.date: 05/14/2019
helpviewer_keywords:
- resource files
- resources [C++]
ms.assetid: 338a4a0f-0c62-4ef1-a34f-5d86262d93a4
ms.openlocfilehash: 20e57aa51cff8c4e3392c313645468387c2a4244
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65707401"
---
# <a name="resource-files-c"></a>Pliki zasobów (C++)

Zasoby są elementy interfejsu, które zawierają informacje do użytkownika. Mapy bitowe, ikony, paski narzędzi i kursory są wszystkie zasoby. Niektóre zasoby można wykonać akcji, takie jak wybór z menu lub wprowadzanie danych w oknie dialogowym.

 Aby uzyskać więcej informacji, zobacz [pracy z zasobami](../../windows/working-with-resource-files.md).

|Nazwa pliku|Lokalizacja katalogu|Lokalizacja Eksploratora rozwiązań|Opis|
|---------------|------------------------|--------------------------------|-----------------|
|*Projname*.rc|*Projname*|Pliki źródłowe|Plik skryptu zasobu dla projektu. Plik skryptu zasobu zawiera następujące polecenie, w zależności od typu projektu i pomocy technicznej, wybrany dla projektu (na przykład, paski narzędzi, okna dialogowe lub HTML):<br /><br />-Definicja menu default.<br />— Tabele akceleratora i ciąg.<br />-Domyślnie **o** okno dialogowe.<br />-Innych oknach dialogowych.<br />-Plik ikony (res\\*Projname*.ico).<br />— Informacje o wersji.<br />-Map bitowych.<br />— Pasek narzędzi.<br />— Pliki HTML.<br /><br /> Plik zasobów zawiera standardowe zasoby MFC w pliku Afxres.rc pliku.|
|Resource.h|*Projname*|Pliki nagłówkowe|Plik nagłówka zasobów zawiera definicje dla zasobów używanych przez projekt.|
|*Projname*.rc2|*Projname*\res|Pliki źródłowe|Plik skryptu zawierający dodatkowe zasoby używane przez projekt. Można dołączyć plik .rc2 w pliku .rc projektu.<br /><br /> Plik .rc2 przydaje się, w tym zasoby używane przez kilka różnych projektach. Nie trzeba tworzyć te same zasoby dla różnych projektów, można umieścić je w pliku .rc2 i dołączyć plik .rc2 w pliku .rc głównego.|
|*Projname*.def|*Projname*|Pliki źródłowe|Plik definicji modułu projektu DLL. W przypadku formantu zawiera nazwę i opis kontrolki, a także rozmiar sterty środowiska wykonawczego.|
|*Projname*.ico|*Projname*\res|Pliki zasobów|Plik ikony dla projektu lub sterowania. Ikona ta pojawia się, gdy aplikacja jest zminimalizowana. Jest również używany w aplikacji **o** pole. Domyślnie biblioteka MFC zawiera ikonę MFC i ATL zawiera ikonę ATL.|
|*Projname*Doc.ico|*Projname*\res|Pliki zasobów|Plik ikony dla projektu MFC, który zawiera obsługę architektury dokumentu/widoku.|
|Toolbar.bmp|*Projname*\res|Pliki zasobów|Plik mapy bitowej reprezentujący aplikacja lub formant paska narzędzi lub palety. Ta mapa bitowa znajduje się w pliku zasobów projektu. Początkowy pasek narzędzi i pasek stanu, które są konstruowane w **cmainframe —** klasy.|
|ribbon.mfcribbon-ms|*Projname*\res|Pliki zasobów|Plik zasobu, który zawiera kod XML, który definiuje przyciskami, formanty i atrybuty na Wstążce. Aby uzyskać więcej informacji, zobacz [Projektant wstążki (MFC)](../../mfc/ribbon-designer-mfc.md).|

## <a name="see-also"></a>Zobacz także

[Plik typy utworzone dla programu Visual Studio C++ projektów](file-types-created-for-visual-cpp-projects.md)
