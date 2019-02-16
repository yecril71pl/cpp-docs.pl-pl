---
title: 'Instrukcje: Dołączanie zasobów w czasie kompilacji (C++)'
ms.date: 02/14/2019
f1_keywords:
- vs.resvw.resource.including
- vc.resvw.resource.including
- vc.editors.resourceincludes
helpviewer_keywords:
- comments [C++], compiled files
- resources [C++], including at compile time
- projects [C++], including resources
- '#include directive'
- include directive (#include)
- Resource Includes dialog box [C++]
- rc files [C++], changing storage
- symbol header files [C++], changing
- .rc files [C++], changing storage
- symbol header files [C++], read-only
- symbols [C++], symbol header files
- directories [C++], specifying include paths for resources
- include files [C++], specifying for resources
- resources [C++], including in projects
- symbols [C++], finding
- resources [C++], searching for symbols
ms.assetid: 357e93c2-0a29-42f9-806f-882f688b8924
ms.openlocfilehash: 06ad2f90e7e72492f1e6ca4000a6c101fc36b205
ms.sourcegitcommit: 470de1337035dd33682d935b4b6c6d8b1bdb0bbb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2019
ms.locfileid: "56320669"
---
# <a name="how-to-include-resources-at-compile-time-c"></a>Instrukcje: Dołączanie zasobów w czasie kompilacji (C++)

Zazwyczaj jest łatwe i wygodne do pracy z domyślnym rozmieszczeniu wszystkich zasobów w jednym pliku skryptu (.rc) zasobu. Jednak istnieje kilka powodów, można umieścić zasoby w pliku innych niż plik .rc główne:

- Aby dodać komentarze do instrukcji zasobów, które nie będą usuwane podczas zapisywania pliku .rc.

   Edytory zasobów bezpośrednio nie czytają .rc lub `resource.h` plików. Kompilator zasobów kompiluje je na .aps pliki, które są używane przez edytory zasobów. Ten plik jest to krok kompilacji i tylko przechowuje dane symboliczne. Jak zwykłym skompilować procesu, informacje, które nie jest symboliczne (na przykład komentarzy) jest pomijany w procesie kompilacji. Zawsze, gdy plik .aps pobiera synchronizację z pliku .rc, zostanie ponownie wygenerowany plik .rc (na przykład, gdy zapisujesz, Edytor zasobów zastępuje plik .rc i `resource.h` pliku). Zmiany wprowadzone w zasobach pozostaną dołączone w pliku .rc, ale komentarze zostać utracone po plik .rc jest zastępowany.

- Aby dołączyć zasoby, które już opracowany i przetestowany i nie wymagają dalszych modyfikacji. (Wszystkie pliki, które są uwzględniane, ale nie ma rozszerzenia .rc nie będzie można edytować za pomocą edytory zasobów).

- Aby dołączyć zasoby, które są używane przez kilku różnych projektów lub należą do systemu kontroli wersji kodu źródłowego, a więc musi istnieć w centralnej lokalizacji, w którym zmiany będzie miało wpływ na wszystkie projekty.

- Aby dołączyć zasoby (na przykład zasoby RCDATA), które znajdują się w niestandardowym formacie. Zasoby RCDATA mogą mieć specjalne wymagania. Na przykład nie można użyć wyrażenia jako wartości dla pola nameID. Aby uzyskać więcej informacji zobacz dokumentację zestawu Windows SDK.

## <a name="resource-includes"></a>Zasób zawiera

Możesz dodać zasoby w innych plikach do bieżącego projektu w czasie kompilacji przez wymienienie ich w **dyrektywy czasu kompilacji** pole w **zasób zawiera** okno dialogowe.

Jeśli masz sekcje w istniejących plikach .rc, które spełniają dowolne z tych warunków sekcje należy umieszczać w jednym lub więcej oddzielnych plików .rc i umieszczone w projekcie za pomocą **zasób zawiera** okno dialogowe. *Projectname*.rc2 utworzone w podkatalogu \res nowy projekt służy do tego celu.

Możesz użyć **zasób zawiera** okno dialogowe w projekcie C++, aby zmodyfikować środowisko normalnej pracy rozmieszczenie przechowywania wszystkich zasobów w pliku .rc projektu, a wszystkie [symbole](../windows/symbols-resource-identifiers.md) w Resource.h.

Aby otworzyć **zasób zawiera** okno dialogowe, kliknij prawym przyciskiem myszy .rc w pliku [widok zasobów](../windows/resource-view-window.md), następnie wybierz **zasób zawiera** z menu skrótów. Zobacz następujące właściwości:

|Właściwość|Opis|
|--|----|
|**Plik nagłówkowy symboli**|Umożliwia zmianę nazwy pliku nagłówkowego, w którym przechowywane są definicje symboli dla Twojego pliku zasobu. Aby uzyskać więcej informacji, zobacz [zmiana nazwy pliki nagłówkowe symboli](../windows/changing-the-names-of-symbol-header-files.md).|
|**Dyrektywy symboli tylko do odczytu**|Można dołączyć plików nagłówkowych, które zawierają symbole, których nie można modyfikować podczas sesji. Na przykład można uwzględnić plik symboli, która jest współużytkowana przez wiele projektów. Może również obejmować pliki .h MFC. Aby uzyskać więcej informacji, zobacz [tym udostępnionych (tylko do odczytu) lub symbole obliczane](../windows/including-shared-read-only-or-calculated-symbols.md).|
|**Dyrektywy czasu kompilacji**|Pozwala dołączyć pliki zasobów, które są tworzone i edytować oddzielnie z zasobów z głównego pliku zasobów, zawierać dyrektywy czasu kompilacji (takich jak te dyrektywy warunkowo obejmujące zasoby) lub zasobów w niestandardowym formacie. Można również użyć **pole dyrektywy czasu kompilacji** obejmujący standardowe pliki zasobów biblioteki MFC.|

> [!NOTE]
> Wpisy w tych polach tekstowych pojawiają się w pliku .rc, oznaczony za `TEXTINCLUDE 1`, `TEXTINCLUDE 2`, i `TEXTINCLUDE 3` odpowiednio. Aby uzyskać więcej informacji, zobacz [TN035: Przy użyciu wielu plików zasobów i plików nagłówków z programem Visual C++](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md).

Po wprowadzeniu zmian do pliku zasobów za pomocą **zasób zawiera** okno dialogowe, należy zamknąć plik .rc i ponownie je, aby zmiany zaczęły obowiązywać.

### <a name="to-include-resources-in-your-project-at-compile-time"></a>Aby dołączyć zasoby do projektu w czasie kompilacji

1. Umieść zasoby w pliku skryptu zasobu przy użyciu unikatowej nazwy pliku. Nie używaj *projectname*.rc, ponieważ ta nazwa jest nazwą pliku używany dla pliku skryptu zasobu głównego.

1. Kliknij prawym przyciskiem myszy plik .rc (w [widok zasobów](../windows/resource-view-window.md)) i wybierz polecenie **zasób zawiera** z menu skrótów.

1. W **dyrektywy czasu kompilacji** Dodaj [#include](../preprocessor/hash-include-directive-c-cpp.md) dyrektywy kompilatora, które mają zostać objęte nowego pliku zasobu z głównego pliku zasobów w środowisku programistycznym.

   Zasoby z plików znajdujących się w ten sposób stają się częścią pliku wykonywalnego w czasie kompilacji. Nie są bezpośrednio dostępne do edycji lub modyfikacji, podczas pracy w pliku .rc głównego projektu. Otwórz pliki .rc dołączony oddzielnie. Wszystkie pliki, które są uwzględniane, ale nie ma rozszerzenia .rc nie będzie można edytować za pomocą edytory zasobów.

### <a name="to-specify-include-directories-for-a-specific-resource-rc-file"></a>Do określenia katalogów dołączanych dla określonego zasobu (plik .rc)

1. Kliknij prawym przyciskiem myszy plik .rc w Eksploratorze rozwiązań i wybierz **właściwości** z menu skrótów.

1. Wybierz **zasobów** węzła w okienku po lewej stronie i określić wszelkie dodatkowe katalogi dołączane we **dodatkowe katalogi dołączane** właściwości.

### <a name="to-find-symbols-in-resources"></a>Aby znaleźć symboli w zasobach

1. Z **Edytuj** menu, wybierz [Znajdź Symbol](/visualstudio/ide/go-to).

1. W **Znajdź** Wybierz poprzedni ciąg wyszukiwania z listy rozwijanej lub wpisz klawisza skrótu do wyszukania (na przykład `ID_ACCEL1`).

   > [!TIP]
   > Aby użyć [wyrażeń regularnych](/visualstudio/ide/using-regular-expressions-in-visual-studio) wyszukiwania, należy użyć [Znajdź w plikach — polecenie](/visualstudio/ide/reference/find-command) z **Edytuj** menu zamiast **Znajdź Symbol**polecenia. Aby włączyć wyrażeń regularnych, konieczne jest posiadanie **użycia: Wyrażenia regularne** zaznaczone pole wyboru w [okno dialogowe Znajdź](/visualstudio/ide/finding-and-replacing-text). Następnie możesz wybrać przycisk strzałki w dół po prawej stronie **Znajdź** pole, aby wyświetlić listę wyrażeń regularnych wyszukiwania. Po wybraniu wyrażenia z tej listy, zostanie zastąpiony jako wyszukiwany tekst w **Znajdź** pole.

1. Wybierz dowolny z **znaleźć** opcje, a następnie wybierz **Znajdź następny**.

> [!NOTE]
> Nie można wyszukiwać symbole w ciągu, akcelerator lub zasobów binarnych.

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Pliki zasobów](../windows/resource-files-visual-studio.md)<br/>
[Tworzenie zasobów](../windows/how-to-create-a-resource-script-file.md)<br/>
[Zarządzanie zasobami](../windows/how-to-copy-resources.md)<br/>