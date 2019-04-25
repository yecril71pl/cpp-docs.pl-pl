---
title: Korzystanie z biblioteki i składników projektów w języku C++
ms.date: 12/10/2018
f1_keywords:
- VC.Project.References
helpviewer_keywords:
- Add References Dialog Box (C++)
- .NET Framework (C++), Add References Dialog Box
ms.assetid: 12b8f571-0f21-40b3-9404-5318a57e9cb5
ms.openlocfilehash: dff057977e6b6ff0c36d3a888bc4d5c3aa778576
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62274792"
---
# <a name="consuming-libraries-and-components"></a>Korzystanie z biblioteki i składniki

Często projektu w języku C++ musi wywoływać funkcje lub dostęp do danych w pliku binarnego, takich jak biblioteka statyczna (.lib pliki), biblioteka DLL składnika środowiska wykonawczego Windows, składnik COM lub zestawu .NET. W takich przypadkach należy skonfigurować projekt, aby ją znaleźć tego pliku binarnego w czasie kompilacji. Konkretne czynności, które zależą od typu projektu, typ danych binarnych, oraz tego, czy plik binarny jest ona kompilowana w taki sposób, w tym samym rozwiązaniu co projekt. 

## <a name="consuming-libraries-downloaded-via-vcpkg"></a>Korzystanie z biblioteki pobrane za pośrednictwem vcpkg

Korzystanie z biblioteki, które zostały pobrane przy użyciu **vcpkg** Menedżera pakietów, można zignorować poniższe instrukcje. See [vcpkg: Menedżer pakietów języka C++ dla Windows, Linux i MacOS](vcpkg.md#integrate-with-visual-studio-windows) Aby uzyskać więcej informacji.

## <a name="consuming-static-libraries"></a>Korzystanie z bibliotek statycznych

Jeśli projekt biblioteki statycznej jest tworzona w tym samym rozwiązaniu:

1. #<a name="include-the-header-files-for-the-static-library-using-quotation-marks-in-a-typical-solution-the-path-will-start-with-library-project-name-intellisense-will-help-you-find-it"></a>obejmują pliki nagłówka dla biblioteki statycznej znaków cudzysłowu. W rozwiązaniu typowych ścieżkę rozpoczyna się od `../<library project name>`. Funkcja IntelliSense ułatwia go znaleźć.
2. Dodaj odwołanie do projektu biblioteki statycznej. Kliknij prawym przyciskiem myszy **odwołania** w węźle projektu aplikacji w **Eksploratora rozwiązań** i wybierz polecenie **Dodaj odwołanie**. 

Jeśli biblioteka statyczna nie jest częścią rozwiązania:

1. Kliknij prawym przyciskiem myszy węzeł projektu aplikacji w **Eksploratora rozwiązań** , a następnie wybierz **właściwości**. 
2. W **katalogi VC ++** właściwości strony, Dodaj ścieżkę do katalogu, w którym plik .lib znajduje się w **ścieżki biblioteki** i dodać ścieżkę do plików nagłówka biblioteki **Dołącz katalogi** .  
3. W **Konsolidator > wejście** właściwości strony, należy dodać nazwę pliku .lib, aby **dodatkowe zależności**.

## <a name="dynamic-link-libraries"></a>Biblioteki łączone dynamicznie

Jeśli biblioteka DLL jest tworzona w ramach tego samego rozwiązania co aplikacja, wykonaj te same czynności, jak w przypadku biblioteki statycznej.

Jeśli biblioteka DLL nie jest częścią rozwiązania aplikacji, potrzebujesz pliku DLL, nagłówków z prototypy wyeksportowanych funkcji i klas, a plik .lib, który dostarcza niezbędne informacje połączeń.

1. Skopiuj do folderu wyjściowego projektu lub do innego folderu w ścieżce wyszukiwania Windows standardowe biblioteki DLL dla bibliotek DLL. Zobacz [kolejności przeszukiwania bibliotek dołączanych dynamicznie](/windows/desktop/dlls/dynamic-link-library-search-order).
2. Wykonaj kroki 1 – 3 bibliotek statycznych zapewnić ścieżki do nagłówków i plik .lib.

## <a name="com-objects"></a>obiekty COM

Jeśli aplikacja natywna C++ musi korzystać z obiektów COM i dany obiekt jest *zarejestrowany*, wszystkie trzeba będzie wywołać CoCreateInstance i przekazać identyfikator CLSID obiektu. System będzie znajduje się w rejestrze systemu Windows i załaduj go. A C++/projekt interfejsu wiersza polecenia mogą wykorzystywać obiektów COM w taki sam sposób, lub przez dodanie odwołania do niego z **Add References > COM** listy i korzystania z nich za pośrednictwem jego [wywoływana otoka środowiska uruchomieniowego](/dotnet/framework/interop/runtime-callable-wrapper). 

## <a name="net-assemblies-and-windows-runtime-components"></a>Zestawy .NET i składników środowiska wykonawczego Windows

W platformy uniwersalnej systemu Windows lub C++projektów w sposób niezamierzony, używanie zestawów platformy .NET lub składników środowiska wykonawczego Windows, dodając *odwołania* do zestawem lub składnikiem. W obszarze **odwołania** węzła w platformy uniwersalnej systemu Windows lub C++sposób niezamierzony projektu, zobacz odwołania do składników często używane. Kliknij prawym przyciskiem myszy **odwołania** w węźle **Eksploratora rozwiązań** aby przywołać **Menadżer odwołań** i przeglądanie dodatkowych składników, które są znane systemowi. Kliknij przycisk **Przeglądaj** przycisk, aby przejść do dowolnego folderu, w którym znajduje się niestandardowy składnik. Ponieważ zestawów platformy .NET i składników środowiska wykonawczego Windows zawierają informacje o typie wbudowane, możesz wyświetlić ich metod i klas, kliknij prawym przyciskiem myszy i wybierając pozycję **Pokaż w przeglądarce obiektów**. 

## <a name="reference-properties"></a>Właściwości odwołania

Każdy rodzaj odwołania ma właściwości. Właściwości można wyświetlić, wybierając odwołania w Eksploratorze rozwiązań i naciskając klawisz **Alt + Enter**, lub kliknąć prawym przyciskiem myszy i wybierając **właściwości**. Niektóre właściwości są tylko do odczytu, a niektóre mogą być modyfikowane. Jednak zazwyczaj nie trzeba ręcznie zmodyfikować te właściwości.

### <a name="activex-reference-properties"></a>Właściwości odwołania ActiveX

Właściwości odwołania ActiveX są dostępne tylko w przypadku odwołania do składników modelu COM. Te właściwości są wyświetlane tylko wtedy, gdy wybrano składnika modelu COM **odwołania** okienka. Nie można zmodyfikować właściwości.

- **Pełna ścieżka kontrolki**

   Wyświetla ścieżkę katalogu przywoływanej kontrolki.

- **Identyfikator GUID kontrolki**

   Wyświetla identyfikator GUID dla formantu ActiveX.

- **Wersja kontrolki**

   Wyświetla wersję przywoływanej kontrolki ActiveX.

- **Nazwa biblioteki typów**

   Nazwa przywoływanej biblioteki typów.

- **Narzędzie otoki**

   Wyświetla narzędzie, które służy do tworzenia zestawu międzyoperacyjnego na podstawie przywoływanej biblioteki COM lub formantu ActiveX.

### <a name="assembly-reference-properties-ccli"></a>Właściwości odwołania do zestawu (C++sposób niezamierzony)

Właściwości odwołania do zestawu są dostępne tylko dla odwołania do zestawów .NET Framework w C++sposób niezamierzony projektów. Te właściwości są wyświetlane tylko w przypadku wybrania w zestawie programu .NET Framework **odwołania** okienka. Nie można zmodyfikować właściwości.

- **Ścieżka względna**

   Wyświetla ścieżkę względną z katalogu projektu do przywoływanego zestawu.

### <a name="build-properties"></a>Właściwości kompilacji

Następujące właściwości są dostępne w różnych rodzajach odwołania. Umożliwiają one określają sposób tworzenia z odwołania.

- **Kopia lokalna**

   Określa, czy ma być automatycznie kopiowany przywoływany zestaw do lokalizacji docelowej podczas kompilacji.

- **Kopiuj lokalne zestawy satelickie (C++sposób niezamierzony)**

   Określa, czy ma być automatycznie kopiowany zestawy satelickie przywoływanego zestawu do lokalizacji docelowej podczas kompilacji. Używany tylko, jeśli **Kopiuj lokalnie** jest **true**.

- **Wyjście zestawu odwołania**

   Określa, że ten zestaw jest używany w procesie kompilacji. Jeśli **true**, zestaw jest używany w wierszu polecenia kompilatora podczas kompilacji.

### <a name="project-to-project-reference-properties"></a>Właściwości odwołania projektu do projektu

Zdefiniuj następujące właściwości *odwołania projekt projekt* z projektu, który wybrano w **odwołania** okienka do innego projektu w tym samym rozwiązaniu. Aby uzyskać więcej informacji, zobacz [Zarządzanie odwołaniami w projekcie](/visualstudio/ide/managing-references-in-a-project).

- **Zależności biblioteki konsolidacji**

   Gdy ta właściwość jest **True**, system projektu łączy do projektu zależnego pliki .lib, które są tworzone przez niezależnych projektu. Zazwyczaj można określić **True**.

- **Identyfikator projektu**

   Jednoznacznie identyfikuje niezależnie od projektu. Wartość właściwości jest systemu wewnętrznego identyfikator GUID, który nie może być modyfikowany.

- **Używaj wejścia zależności biblioteki**

   Gdy ta właściwość jest **False**, system projektu nie połączy do projektu zależnego pliki .obj dla biblioteki utworzony przez projekt niezależny. W związku z tym wartość ta wyłącza łączenie przyrostowe. Zazwyczaj można określić **False** ponieważ Kompilowanie aplikacji może zająć dużo czasu, jeśli istnieje wiele projektów niezależnych.

### <a name="read-only-reference-properties-com--net"></a>Właściwości odwołań tylko do odczytu (COM i .NET)

Następujące właściwości znajdują się na odwołania do zestawu modelu COM i .NET, a nie może być modyfikowany.

- **Nazwa zestawu**

   Wyświetla nazwę zestawu dla przywoływanego zestawu.

- **Kultury**

   Wyświetla kultura wybranego odwołania.

- **Opis**

   Wyświetla opis wybranego odwołania.

- **Pełna ścieżka**

   Wyświetla ścieżkę katalogu przywoływanego zestawu.

- **Tożsamość**

   W przypadku Frameworkassemblies .NET Wyświetla pełną ścieżkę. Dla składników modelu COM Wyświetla identyfikator GUID.

- **Etykieta**

   Wyświetla etykieta odwołania.

- **Nazwa**

   Wyświetla nazwę odwołania.

- **Token klucza publicznego**

   Wyświetla token klucza publicznego, który służy do identyfikowania przywoływanego zestawu.

- **Silna nazwa**

   `true` Jeśli przywoływany zestaw ma silną nazwę. Silną nazwą ma unikatową wersję.

- **Wersja**

   Wyświetla wersję przywoływanego zestawu.

## <a name="see-also"></a>Zobacz także

[Dokumentacja strony właściwości projektu C++](reference/property-pages-visual-cpp.md)<br>
[Ustawianie właściwości kompilacji i kompilatora języka C++ w programie Visual Studio](working-with-project-properties.md)