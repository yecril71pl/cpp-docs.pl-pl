---
title: 'Instrukcje: Zarządzanie symbolami'
ms.date: 02/14/2019
f1_keywords:
- vc.editors.symbol.changing
- vc.editors.symbol.restrictions.name
- vc.editors.symbol.changing.value
- vc.editors.symbol.restrictions.value
- vc.editors.symbol.changing.header
- vc.editors.symbol.changing.unassigned
- vc.editors.symbol.shared.calculated
helpviewer_keywords:
- symbol names
- symbols [C++], names
- restrictions, symbol names
- numeric values
- symbols [C++], numeric values
- numeric values, changing symbols
- symbols [C++], value restrictions
- restrictions, symbol values
- resource files [C++], multiple
- Resource Includes dialog box [C++]
- symbol header files [C++], changing names
- symbols [C++], symbol header files
- Resource.h
- symbols [C++], unassigned
- Change Symbol dialog box [C++]
- unassigned symbols
- symbols [C++], deleting
- symbols [C++], read-only
- symbols [C++], shared
- symbols [C++], calculated
- read-only symbols
- symbol directives
- calculated symbols
- shared symbols
ms.assetid: 26541832-8dba-4177-b642-e08f94502ea7
ms.openlocfilehash: 67a5c801c13038e7215473edecc2d41a8f7086e0
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91505726"
---
# <a name="how-to-manage-symbols"></a>Instrukcje: Zarządzanie symbolami

Podczas tworzenia nowego zasobu lub obiektu zasobu środowisko programistyczne przypisuje mu domyślną nazwę symbolu, na przykład `IDD_DIALOG1` . Za pomocą [okno właściwości](/visualstudio/ide/reference/properties-window) można zmienić domyślną nazwę symbolu lub zmienić nazwę dowolnego symbolu, który jest już skojarzony z zasobem.

W przypadku symboli skojarzonych z pojedynczym zasobem można także użyć okna **Właściwości** , aby zmienić wartość symbolu. Za pomocą [okna dialogowego symbole zasobów](./creating-new-symbols.md) można zmienić wartość symboli, które nie są aktualnie przypisane do zasobu.

Zwykle wszystkie definicje symboli są zapisywane w `Resource.h` . Może jednak być konieczna zmiana nazwy pliku dołączanego, aby można było na przykład współpracować z więcej niż jednym plikiem zasobów w tym samym katalogu.

> [!NOTE]
> Jeśli projekt nie zawiera jeszcze pliku. RC, zobacz [How to: Create Resources](how-to-create-a-resource-script-file.md).

## <a name="symbol-name-restrictions"></a>Ograniczenia dotyczące nazwy symbolu

Ograniczenia dotyczące nazw symboli są następujące:

- Wszystkie [symbole](symbols-resource-identifiers.md) muszą być unikatowe w obrębie zakresu aplikacji, aby zapobiec sprzecznym definicjami symboli w plikach nagłówkowych.

- Prawidłowe znaki nazwy symbolu obejmują A-Z, a-z, 0-9 i podkreślenia (_).

- Nazwy symboli nie mogą rozpoczynać się od cyfry i są ograniczone do 247 znaków.

- Nazwy symboli nie mogą zawierać spacji.

- W nazwach symboli nie jest rozróżniana wielkość liter, ale wielkość liter w pierwszej definicji symbolu jest zachowywana.

   Plik nagłówkowy definiujący symbole jest używany przez kompilator/Edytor zasobów i programy języka C++ do odwoływania się do zasobów zdefiniowanych w pliku zasobów. Dla dwóch nazw symboli, które różnią się tylko wielkością liter, program C++ zobaczy dwa osobne symbole, podczas gdy kompilator zasobów/Edytor będzie widział obie nazwy w odniesieniu do jednego pojedynczego symbolu.

> [!NOTE]
> Jeśli nie obserwujesz standardowego schematu nazw symboli (identyfikator * _ [słowo kluczowe]) przedstawiony poniżej, a nazwa symbolu ma być taka sama jak słowo kluczowe znane do kompilatora skryptów zasobów, Próba skompilowania pliku skryptu zasobu spowoduje pozornie losowe generowanie błędów, co jest trudne do zdiagnozowania. Aby tego uniknąć, należy przestrzegać standardowego schematu nazewnictwa.

Nazwy symboli mają opisowe prefiksy wskazujące rodzaj zasobów lub obiektów, które reprezentują. Te prefiksy opisowe zaczynają się od identyfikatora kombinacji tekstu. Biblioteka Microsoft Foundation Class (MFC) używa konwencji nazewnictwa symboli pokazanych w poniższej tabeli:

|Kategoria|Prefiks|Zastosowanie|
|--------------|------------|---------|
|Zasoby|IDR_, IDD_, IDC_, IDI_, IDB_|Akcelerator lub menu (oraz skojarzone lub niestandardowe zasoby), okno dialogowe, kursor, ikona, mapa bitowa|
|Elementy menu|ID_|Element menu|
|Polecenia|ID_|Polecenie|
|Kontrolki i okna podrzędne|IDC_|Kontrola|
|Ciągi|IDS_|Ciąg w tabeli ciągów|
|MFC|AFX_|Zarezerwowane dla wstępnie zdefiniowanych symboli MFC|

### <a name="to-change-a-symbol-name-id"></a>Aby zmienić nazwę symbolu (ID)

1. W obszarze [Widok zasobów](how-to-create-a-resource-script-file.md#create-resources)wybierz zasób.

1. W oknie **Właściwości** wpisz nową nazwę symbolu lub wybierz z listy istniejących symboli w polu **ID** .

   Wpisanie nowej nazwy symbolu powoduje automatyczne przypisanie wartości.

> [!NOTE]
> Za pomocą [okna dialogowego symbole zasobów](./creating-new-symbols.md) można zmienić nazwy symboli, które nie są aktualnie przypisane do zasobu.

## <a name="symbol-value-restrictions"></a>Ograniczenia dotyczące wartości symbolu

Wartość symbolu może być dowolną liczbą całkowitą wyrażoną w normalny sposób dla `#define` dyrektyw preprocesora. Poniżej przedstawiono kilka przykładów wartości symboli:

```
18
4001
0x0012
-3456
```

Wartości symboli dla zasobów takich jak akceleratory, mapy bitowe, kursory, okna dialogowe, ikony, menu, tabele ciągów i informacje o wersji muszą być liczbami dziesiętnymi z zakresu od 0 do 32 767, ale nie może być szesnastkowa. Wartości symboli dla części zasobów, takich jak kontrolki okna dialogowego lub poszczególne ciągi w tabeli ciągów, mogą mieć wartość z przedziału od 0 do 65 534 lub z-32 768 do 32 767. Aby uzyskać więcej informacji o zakresach liczbowych, zobacz [TN023: standardowe zasoby MFC](../mfc/tn023-standard-mfc-resources.md).

Symbole zasobów są liczbami 16-bitowymi. Można je wprowadzić jako podpisane lub niepodpisane, ale są one używane wewnętrznie jako liczby całkowite bez znaku, więc liczby ujemne będą rzutowane na odpowiadające im wartości dodatnie.

Niektóre ograniczenia dotyczące wartości symboli są następujące:

- Środowisko deweloperskie programu Visual Studio i MFC używają niektórych zakresów liczbowych do specjalnych celów. Wszystkie liczby z najbardziej znaczącym zestawem bitów (-32 768 do-1 lub 32 768 do 65 534, w zależności od znaku) są zarezerwowane przez MFC.

- Nie można zdefiniować wartości symbolu przy użyciu innych ciągów symboli. Na przykład następująca definicja symbolu nie jest obsługiwana:

    ```cpp
    #define IDC_MYEDIT  IDC_OTHEREDIT  //not supported
    ```

- Nie można użyć makr preprocesora z argumentami jako definicje wartości. Poniższy przykład nie jest prawidłowym wyrażeniem, bez względu na to, co `ID` szacuje się w czasie kompilacji:

    ```cpp
    #define   IDD_ABOUT  ID(7) //not supported
    ```

- Twoja aplikacja może mieć istniejący plik zawierający symbole zdefiniowane za pomocą wyrażeń.

### <a name="to-change-a-symbol-value"></a>Aby zmienić wartość symbolu

1. W obszarze [Widok zasobów](how-to-create-a-resource-script-file.md#create-resources)wybierz zasób.

1. W oknie **Właściwości** wpisz nazwę symbolu, a po nim znak równości i liczbę całkowitą w polu **Identyfikator** , na przykład:

    ```
    IDC_EDITNAME=5100
    ```

   Nowa wartość jest przechowywana w pliku nagłówkowym symboli przy następnym zapisaniu projektu. Tylko nazwa symbolu pozostaje widoczna w polu ID, a znak równości i wartość nie będą wyświetlane po sprawdzeniu poprawności.

## <a name="change-or-delete-symbols"></a>Zmień lub Usuń symbole

W [oknie dialogowym symbole zasobów](./creating-new-symbols.md)można edytować lub usuwać istniejące symbole, które nie są już przypisane do zasobu lub obiektu.

### <a name="to-change-an-unassigned-symbol"></a>Aby zmienić nieprzypisany symbol

1. W polu **Nazwa** wybierz nieprzypisany symbol i wybierz pozycję **Zmień**.

1. Edytuj nazwę lub wartość symbolu w polach, które znajdują się w oknie dialogowym **Zmień symbol** .

> [!NOTE]
> Aby zmienić symbol przypisany do zasobu lub obiektu, należy użyć edytora zasobów lub okna **Właściwości** .

### <a name="to-delete-an-unassigned-unused-symbol"></a>Aby usunąć nieprzypisany symbol (nieużywany)

W oknie dialogowym **symbole zasobów** wybierz symbol, który chcesz usunąć, a następnie wybierz pozycję **Usuń**.

> [!NOTE]
> Przed usunięciem nieużywanego symbolu w pliku zasobów upewnij się, że nie jest on używany w innym miejscu w programie ani w plikach zasobów uwzględnionych w czasie kompilacji.

## <a name="include-symbols"></a>Dołącz symbole

Gdy środowisko programistyczne odczytuje plik zasobów utworzony przez inną aplikację, oznacza wszystkie dołączone pliki nagłówkowe jako tylko do odczytu. Chociaż możesz użyć [okna dialogowego zasób zawiera](./how-to-include-resources-at-compile-time.md) , aby dodać dodatkowe pliki nagłówka symboli tylko do odczytu.

Jedną z przyczyn może być użycie definicji symboli tylko do odczytu dla plików symboli, które planujesz udostępnić między kilka projektów.

Można również użyć dołączonych plików symboli, jeśli masz istniejące zasoby z definicjami symboli, które używają wyrażeń zamiast prostych liczb całkowitych, aby zdefiniować wartość symbolu. Na przykład:

```cpp
#define   IDC_CONTROL1 2100
#define   IDC_CONTROL2 (IDC_CONTROL1+1)
```

Środowisko będzie poprawnie interpretować te symbole obliczeniowe tak długo, jak:

- Symbole obliczeniowe są umieszczane w pliku symboli tylko do odczytu.

- Plik zasobów zawiera zasoby, do których zostały już przypisane te symbole obliczeniowe.

- Oczekiwano wyrażenia liczbowego.

> [!NOTE]
> Jeśli oczekiwano ciągu lub wyrażenia liczbowego, wyrażenie nie jest oceniane.

### <a name="to-include-shared-read-only-symbols-in-your-resource-file"></a>Aby uwzględnić udostępnione symbole (tylko do odczytu) w pliku zasobów

1. W [Widok zasobów](how-to-create-a-resource-script-file.md#create-resources)kliknij prawym przyciskiem myszy plik *. RC* , a następnie wybierz pozycję [zasób zawiera](./how-to-include-resources-at-compile-time.md).

1. W polu **dyrektywy symboli tylko do odczytu** Użyj `#include` dyrektywy kompilatora, aby określić plik, w którym mają zostać zachowane symbole tylko do odczytu.

   Nie wywołuj pliku `Resource.h` , ponieważ jest to nazwa pliku zwykle używana przez główny plik nagłówka symboli.

   > [!NOTE]
   > Wpisany tekst w polu **dyrektywy symboli tylko do odczytu** jest dołączany do pliku zasobu dokładnie podczas jego wpisywania. Upewnij się, że typ nie zawiera żadnych błędów pisowni ani składni.

   Użyj pola **dyrektywy symboli tylko do odczytu** w celu uwzględnienia tylko plików z definicjami symboli. Nie dołączaj definicji zasobów, w przeciwnym razie podczas zapisywania pliku zostaną utworzone zduplikowane definicje zasobów.

1. Umieść symbole w określonym pliku.

   Symbole w plikach zawartych w ten sposób są oceniane przy każdym otwarciu pliku zasobów, ale nie są one zastępowane na dysku podczas zapisywania pliku.

1. Wybierz przycisk **OK**.

### <a name="to-change-the-name-of-the-resource-symbol-header-file"></a>Aby zmienić nazwę pliku nagłówkowego symboli zasobów

1. W [Widok zasobów](how-to-create-a-resource-script-file.md#create-resources)kliknij prawym przyciskiem myszy plik *. RC* , a następnie wybierz pozycję [zasób zawiera](./how-to-include-resources-at-compile-time.md).

1. W polu **plik nagłówka symbolu** wpisz nową nazwę dla pliku dołączanego.

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Identyfikatory zasobów (symbole)](symbols-resource-identifiers.md)<br/>
[Instrukcje: Tworzenie symboli](creating-new-symbols.md)<br/>
[Wstępnie zdefiniowane identyfikatory symboli](predefined-symbol-ids.md)<br/>
