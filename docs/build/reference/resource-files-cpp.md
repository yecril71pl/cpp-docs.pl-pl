---
title: Pliki zasobów projektu (C++)
ms.date: 05/14/2019
helpviewer_keywords:
- resource files
- resources [C++]
ms.assetid: 338a4a0f-0c62-4ef1-a34f-5d86262d93a4
ms.openlocfilehash: d37c3602d8939db609fc8af42dd764655195b24b
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2020
ms.locfileid: "90041019"
---
# <a name="project-resource-files-c"></a>Pliki zasobów projektu (C++)

Zasoby są elementami interfejsu, które zawierają informacje dla użytkownika. Mapy bitowe, ikony, paski narzędzi i kursory są wszystkie zasobami. Niektóre zasoby mogą wykonywać akcje, takie jak wybór z menu lub wprowadzanie danych w oknie dialogowym.

Aby uzyskać więcej informacji, zobacz [Praca z zasobami](../../windows/working-with-resource-files.md).

|Nazwa pliku|Lokalizacja katalogu|Lokalizacja Eksplorator rozwiązań|Opis|
|---------------|------------------------|--------------------------------|-----------------|
|*Projname*. RC|*Projname*|Pliki źródłowe|Plik skryptu zasobu dla projektu. Plik skryptu zasobu zawiera następujące, w zależności od typu projektu, i pomoc techniczną wybraną dla projektu (na przykład paski narzędzi, okna dialogowe lub HTML):<br /><br />— Domyślna definicja menu.<br />-Akcelerator i tabele ciągów.<br />-Domyślne **Informacje o** oknie dialogowym.<br />— Inne okna dialogowe.<br />-— Plik ikony (res \\ *Projname*. ico).<br />— Informacje o wersji.<br />Mapy bitowe.<br />Pasku narzędzi.<br />— Pliki HTML.<br /><br /> Plik zasobów zawiera plik plik AFXRES. RC dla standardowych zasobów klasy Microsoft Foundation.|
|Resource.h|*Projname*|Pliki nagłówkowe|Plik nagłówka zasobu zawierający definicje zasobów używanych przez projekt.|
|*Projname*. RC2|*Projname*\res|Pliki źródłowe|Plik skryptu zawierający dodatkowe zasoby używane przez ten projekt. W pliku. rc projektu można uwzględnić plik. RC2.<br /><br /> Plik. RC2 jest przydatny do uwzględnienia zasobów używanych przez kilka różnych projektów. Zamiast konieczności tworzenia tych samych zasobów kilka razy dla różnych projektów, można umieścić je w pliku. RC2 i dołączyć plik. RC2 do głównego pliku. rc.|
|*Projname*. def|*Projname*|Pliki źródłowe|Plik definicji modułu dla projektu DLL. Dla kontrolki zawiera nazwę i opis kontrolki, a także rozmiar sterty czasu wykonywania.|
|*Projname*. ico|*Projname*\res|Pliki zasobów|Plik ikony dla projektu lub formantu. Ta ikona jest wyświetlana, gdy aplikacja jest zminimalizowana. Jest również używany w oknie **Informacje o** aplikacji. Domyślnie MFC zawiera ikonę MFC, a ATL zawiera ikonę ATL.|
|*Projname* Doc. ico|*Projname*\res|Pliki zasobów|Plik ikony dla projektu MFC, który obejmuje obsługę architektury dokument/widok.|
|Toolbar.bmp|*Projname*\res|Pliki zasobów|Plik mapy bitowej reprezentujący aplikację lub kontrolkę na pasku narzędzi lub w palecie. Ta mapa bitowa jest zawarta w pliku zasobów projektu. Początkowy pasek narzędzi i pasek stanu są skonstruowane w klasie **CMainFrame** .|
|Wstążka. mfcribbon — ms|*Projname*\res|Pliki zasobów|Plik zasobu, który zawiera kod XML, który definiuje przyciski, kontrolki i atrybuty na Wstążce. Aby uzyskać więcej informacji, zobacz [Projektant wstążki (MFC)](../../mfc/ribbon-designer-mfc.md).|

## <a name="see-also"></a>Zobacz także

[Typy plików utworzone dla projektów Visual Studio C++](file-types-created-for-visual-cpp-projects.md)
