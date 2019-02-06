---
title: Zmienianie symbolu
ms.date: 11/04/2016
f1_keywords:
- vc.editors.symbol.changing
- vc.editors.symbol.restrictions.name
- vc.editors.symbol.changing.value
- vc.editors.symbol.restrictions.value
- vc.editors.symbol.changing.header
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
ms.assetid: 26541832-8dba-4177-b642-e08f94502ea7
ms.openlocfilehash: 7d2890c2d2c05f1ee0309446dfe2de9917f85707
ms.sourcegitcommit: 63c072f5e941989636f5a2b13800b68bb7129931
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/06/2019
ms.locfileid: "55763989"
---
# <a name="changing-a-symbol"></a>Zmienianie symbolu

Podczas tworzenia nowego zasobu lub obiektu zasobu, środowisko programistyczne przypisuje mu nazwę symbolu domyślną, na przykład IDD_DIALOG1. Możesz użyć [okno właściwości](/visualstudio/ide/reference/properties-window) zmienić domyślną nazwę symbolu lub zmień nazwę symbolu już skojarzony z zasobem.

Dla symboli skojarzone z pojedynczego zasobu, można również użyć **właściwości** okna, aby zmienić wartość symbol. Możesz użyć [okno dialogowe symboli zasobów](../windows/resource-symbols-dialog-box.md) zmianę wartości symboli nie jest aktualnie przypisany do zasobu. Aby uzyskać więcej informacji, zobacz [zmiana nieprzypisanych symboli](../windows/changing-unassigned-symbols.md).

Zwykle symbol wszystkie definicje są zapisywane w `Resource.h`. Może jednak może być konieczna zmiana to zawierać nazwę pliku na przykład korzystania z więcej niż jeden plik zasobów w tym samym katalogu.

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*.

## <a name="to-change-a-resources-symbol-name-id"></a>Aby zmienić zasób nazwy symbolu (ID)

1. W [widok zasobów](../windows/resource-view-window.md), wybierz zasób.

   > [!NOTE]
   > Jeśli projekt nie zawiera jeszcze pliku .rc, zobacz [tworzenia nowego pliku skryptu zasobów](../windows/how-to-create-a-resource-script-file.md).

1. W **właściwości** okna, wpisz nową nazwę symbolu lub wybierz z listy istniejących symboli w **identyfikator** pole.

   Jeśli wpiszesz nową nazwę symbolu, jest automatycznie przypisywany wartość.

Możesz użyć [okno dialogowe symboli zasobów](../windows/resource-symbols-dialog-box.md) się zmienić nazwy symboli nie jest aktualnie przypisany do zasobu. Aby uzyskać więcej informacji, zobacz [zmiana nieprzypisanych symboli](../windows/changing-unassigned-symbols.md).

### <a name="symbol-name-restrictions"></a>Ograniczenia dotyczące nazwy symbolu

Ograniczenia dotyczące nazwy symbolu są następujące:

- Wszystkie [symbole](../windows/symbols-resource-identifiers.md) musi być unikatowa w zakresie aplikacji. Zapobiega to sprzecznych definicji symbolu w plikach nagłówkowych.

- Nieprawidłowe znaki dla nazwy symbolu to A-Z, a – z, 0-9 i znaki podkreślenia (_).

- Nazwy symboli nie może zaczynać się liczbą i są ograniczone do 247 znaków.

- Nazwy symboli nie może zawierać spacji.

- Nazwy symboli nie jest uwzględniana wielkość liter, ale są zachowywane w przypadku pierwszej definicji symbolu. Plik nagłówka, który definiuje symbole jest używany przez kompilator/Edytor zasobów i C++ programy do odwoływania się zasoby zdefiniowane w pliku zasobów. Dwie nazwy symbolu które różnią się, tylko w przypadku, program w języku C++ zostanie wyświetlony dwa oddzielne symbole, gdy kompilator/Edytor zasobów zostanie wyświetlony obie nazwy jako odnoszące się do jednego pojedynczego symbolu.

   > [!NOTE]
   > Jeśli nie podlegają schemat nazwę standardowego symbolu (ID*_[keyword]) opisane poniżej, a Twoja nazwa symbolu stanie się być taka sama jak słowo kluczowe wiadomo, że kompilator skryptu zasobów, próba skompilowania pliku skryptu zasobu spowoduje błąd pozornie losowe Generowanie, który jest trudny do zdiagnozowania. Aby tego uniknąć, należy przestrzegać standardowych schemat nazewnictwa.

Nazwy symboli ma opisowe prefiksy, które wskazują rodzaj zasobu lub obiektów, które reprezentują. Prefiksy te opisowy zaczynają się od identyfikatora kombinację tekstu Biblioteka Microsoft Foundation Class (MFC) używa konwencji nazewnictwa symbol pokazano w poniższej tabeli.

|Kategoria|Prefiks|Zastosowanie|
|--------------|------------|---------|
|Resources|IDR_ IDD_ IDC_ IDI_ IDB_|Akcelerator lub menu (i skojarzone lub niestandardowe zasoby) okno dialogowe mapę bitową ikony kursora|
|Elementy menu|ID_|Element menu|
|Polecenia|ID_|Polecenie|
|Formanty i okien podrzędnych|IDC_|Formant|
|Ciągi|IDS_|Parametry w tabeli ciągów|
|MFC|AFX_|Zarezerwowane dla wstępnie zdefiniowane symbole MFC|

## <a name="to-change-a-symbol-value-assigned-to-a-single-resource-or-object"></a>Aby zmienić wartość symbol przypisane do jednego zasobu lub obiektu

1. W [widok zasobów](../windows/resource-view-window.md), wybierz zasób.

   > [!NOTE]
   > Jeśli projekt nie zawiera jeszcze pliku .rc, zobacz [tworzenia nowego pliku skryptu zasobów](../windows/how-to-create-a-resource-script-file.md).

1. W **właściwości** okna, typ nazwy symbolu następuje znak równości i całkowitą **identyfikator** polu, na przykład:

    ```
    IDC_EDITNAME=5100
    ```

Nowa wartość są przechowywane w pliku nagłówkowym symboli podczas następnego zapisany projekt. Tylko nazwa symbolu pozostaje widoczna w polu Identyfikator; znak równości i wartości nie są wyświetlane po ich są prawidłowe.

### <a name="symbol-value-restrictions"></a>Ograniczenia dotyczące wartości symbolu

Wartością symboliczną, może być liczbą całkowitą, wyrażone w normalny sposób do #define dyrektywy preprocesora. Poniżej przedstawiono kilka przykładów wartości symboli:

```
18
4001
0x0012
-3456
```

Wartości symboli dla zasobów (akceleratorów, mapy bitowe, kursorów, okna dialogowe, ikony, menu, tabele ciągów i informacje o wersji) muszą być liczbami dziesiętnymi z zakresu od 0 do 32 767 (ale nie może być szesnastkowym). Wartości symboli dla części zasobów, takich jak formanty okna dialogowego lub poszczególne ciągi w tabeli ciągów może być z zakresu od 0 do 65,534 lub od-32 768 do 32 767 znaków.

Symbole zasobów to 16-bitowych liczb. Można je wprowadzić jako podpisane lub niepodpisane, jednak są one używane wewnętrznie jako liczb całkowitych bez znaku. Dlatego wartości ujemne będzie można rzutować na ich odpowiednich wartości dodatniej.

Poniżej przedstawiono pewne ograniczenia wartości symboli:

- Środowisko projektowe programu Visual Studio i MFC na użytek niektóre liczba zakresów specjalnych celów. Wszystkie liczby z zestawem najbardziej znaczący bit (-32 768 -1 lub 32768 do 65,534, w zależności od logowania) są zarezerwowane przez MFC.

- Nie można zdefiniować wartości symboliczną za pomocą innych ciągów symboli. Na przykład następująca definicja symbol nie jest obsługiwana:

    ```cpp
    #define IDC_MYEDIT  IDC_OTHEREDIT  //not supported
    ```

- Nie można użyć makra preprocesora z argumentami, jako wartość definicje. Na przykład:

    ```cpp
    #define   IDD_ABOUT  ID(7) //not supported
    ```

   nie jest prawidłowym wyrażeniem niezależnie od tego, co `ID` daje w wyniku w czasie kompilacji.

- Aplikacja może mieć istniejący plik zawierający symboli zdefiniowanych za pomocą wyrażeń. Aby uzyskać więcej informacji na temat sposobu dołączać symbole jako symbole tylko do odczytu, zobacz [przy użyciu udostępnionych (tylko do odczytu) lub symbole obliczane](../windows/including-shared-read-only-or-calculated-symbols.md).

Aby uzyskać więcej informacji na temat zakresów liczb, zobacz [TN023: Standardowe zasoby MFC](../mfc/tn023-standard-mfc-resources.md).

## <a name="to-change-the-name-of-the-resource-symbol-header-file"></a>Aby zmienić nazwę pliku nagłówkowego symboli zasobów

1. W [widok zasobów](../windows/resource-view-window.md), kliknij prawym przyciskiem myszy plik .rc i wybierz [zasób zawiera](../windows/resource-includes-dialog-box.md) z menu skrótów.

   > [!NOTE]
   > Jeśli projekt nie zawiera jeszcze pliku .rc, zobacz [tworzenia nowego pliku skryptu zasobów](../windows/how-to-create-a-resource-script-file.md).

1. W **plik nagłówka symbolu** wpisz nową nazwę dla pliku dyrektywy include.

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz także

[Wstępnie zdefiniowane identyfikatory symboli](../windows/predefined-symbol-ids.md)<br/>
[Wyświetlanie symboli zasobów](../windows/viewing-resource-symbols.md)<br/>
