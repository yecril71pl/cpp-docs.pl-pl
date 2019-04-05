---
title: 'Instrukcje: Zarządzanie symboli'
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
ms.openlocfilehash: ebf10ade734d321c5a83644110d3511e4b6c827a
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59033998"
---
# <a name="how-to-manage-symbols"></a>Instrukcje: Zarządzanie symboli

Podczas tworzenia nowego zasobu lub obiektu zasobu, środowisko programistyczne przypisuje mu domyślnej nazwy symbolu, na przykład `IDD_DIALOG1`. Możesz użyć [okno właściwości](/visualstudio/ide/reference/properties-window) zmienić domyślną nazwę symbolu lub zmień nazwę symbolu już skojarzony z zasobem.

Dla symboli skojarzone z pojedynczego zasobu, można również użyć **właściwości** okna, aby zmienić wartość symbol. Możesz użyć [okno dialogowe symboli zasobów](../windows/resource-symbols-dialog-box.md) zmianę wartości symboli nie jest aktualnie przypisany do zasobu.

Zwykle symbol wszystkie definicje są zapisywane w `Resource.h`. Może jednak może być konieczna zmiana to zawierać nazwę pliku na przykład korzystania z więcej niż jeden plik zasobów w tym samym katalogu.

> [!NOTE]
> Jeśli projekt nie zawiera jeszcze pliku .rc, zobacz [jak: Tworzenie zasobów](../windows/how-to-create-a-resource-script-file.md).

## <a name="symbol-name-restrictions"></a>Ograniczenia dotyczące nazwy symbolu

Ograniczenia dotyczące nazwy symbolu są następujące:

- Wszystkie [symbole](../windows/symbols-resource-identifiers.md) musi być unikatowa w zakresie aplikacji, aby zapobiec sprzecznych definicji symbolu w plikach nagłówkowych.

- Nieprawidłowe znaki dla nazwy symbolu to A-Z, a – z, 0-9 i znaki podkreślenia (_).

- Nazwy symboli nie może zaczynać się liczbą i są ograniczone do 247 znaków.

- Nazwy symboli nie może zawierać spacji.

- Nazwy symboli nie uwzględniana wielkość liter, ale są zachowywane w przypadku pierwszej definicji symbolu.

   Plik nagłówka, który definiuje symbole jest używany przez kompilator/Edytor zasobów i C++ programy do odwoływania się zasoby zdefiniowane w pliku zasobów. Dwie nazwy symbolu które różnią się, tylko w przypadku, program w języku C++ zostanie wyświetlony dwa oddzielne symbole, gdy kompilator/Edytor zasobów zostanie wyświetlony obie nazwy jako odnoszące się do jednego pojedynczego symbolu.

> [!NOTE]
> Jeśli nie zgodnie ze schematem nazwę standardowego symbolu (ID*_[keyword]) opisane poniżej i nazwę symbolu stanie się być taka sama jak słowo kluczowe wiadomo, że kompilator skryptu zasobów, próba skompilowania pliku skryptu zasobu spowoduje błąd pozornie losowe generowanie który jest trudny do zdiagnozowania. Aby tego uniknąć, należy przestrzegać standardowych schemat nazewnictwa.

Nazwy symboli ma opisowe prefiksy, które wskazują rodzaj zasobu lub obiektów, które reprezentują. Prefiksy te opisowy zaczynają się od identyfikatora kombinację tekstu Biblioteka Microsoft Foundation Class (MFC) używa symbol poniższą tabelą konwencji nazewnictwa:

|Kategoria|Prefiks|Zastosowanie|
|--------------|------------|---------|
|Zasoby|IDR_, IDD_, IDC_, IDI_, IDB_|Akcelerator lub menu (i skojarzone lub niestandardowe zasoby), okno dialogowe, kursor, ikony, mapy bitowej|
|Elementy menu|ID_|Element menu|
|Polecenia|ID_|Polecenie|
|Formanty i okien podrzędnych|IDC_|formant|
|Ciągi|IDS_|Parametry w tabeli ciągów|
|MFC|AFX_|Zarezerwowane dla wstępnie zdefiniowane symbole MFC|

### <a name="to-change-a-symbol-name-id"></a>Aby zmienić nazwę symbolu (ID)

1. W [widok zasobów](how-to-create-a-resource-script-file.md#create-resources), wybierz zasób.

1. W **właściwości** okna, wpisz nową nazwę symbolu lub wybierz z listy istniejących symboli w **identyfikator** pole.

   Jeśli wpiszesz nową nazwę symbolu, automatycznie przypisał wartości.

> [!NOTE]
> Możesz użyć [okno dialogowe symboli zasobów](../windows/resource-symbols-dialog-box.md) się zmienić nazwy symboli nie jest aktualnie przypisany do zasobu.

## <a name="symbol-value-restrictions"></a>Ograniczenia dotyczące wartości symbolu

Wartością symboliczną, może być liczbą całkowitą, wyrażone w normalny sposób dla `#define` dyrektywy preprocesora. Poniżej przedstawiono kilka przykładów wartości symboli:

```
18
4001
0x0012
-3456
```

Wartości symboli dla zasobów, takich jak akceleratorów, mapy bitowe, kursorów, okna dialogowe, ikony, menu, tabele ciągów i wersji informacji, muszą być liczbami dziesiętnymi z zakresu od 0 do 32 767, ale nie może być szesnastkowe. Wartości symboli dla części zasobów, takich jak formanty okna dialogowego lub poszczególne ciągi w tabeli ciągów może być z zakresu od 0 do 65,534 lub od-32 768 do 32 767 znaków. Aby uzyskać więcej informacji na temat zakresów liczb, zobacz [TN023: Standardowe zasoby MFC](../mfc/tn023-standard-mfc-resources.md).

Symbole zasobów są 16-bitowymi liczbami. Można je wprowadzić jako podpisane lub niepodpisane, jednak są używane wewnętrznie jako liczb całkowitych bez znaku, dzięki czemu będzie można rzutować wartości ujemne ich odpowiednich wartości dodatniej.

Niektóre ograniczenia wartości symboli są:

- Środowisko projektowe programu Visual Studio i MFC na użytek niektóre liczba zakresów specjalnych celów. Wszystkie liczby z zestawem najbardziej znaczący bit (-32 768 -1 lub 32768 do 65,534, w zależności od logowania) są zarezerwowane przez MFC.

- Nie można zdefiniować wartości symboliczną za pomocą innych ciągów symboli. Na przykład następująca definicja symbol nie jest obsługiwane:

    ```cpp
    #define IDC_MYEDIT  IDC_OTHEREDIT  //not supported
    ```

- Nie można użyć makra preprocesora z argumentami, jako wartość definicje. Poniższy przykład nie jest prawidłowym wyrażeniem niezależnie od tego, co `ID` daje w wyniku w czasie kompilacji:

    ```cpp
    #define   IDD_ABOUT  ID(7) //not supported
    ```

- Aplikacja może mieć istniejący plik zawierający symboli zdefiniowanych za pomocą wyrażeń.

### <a name="to-change-a-symbol-value"></a>Aby zmienić wartości symbolu

1. W [widok zasobów](how-to-create-a-resource-script-file.md#create-resources), wybierz zasób.

1. W **właściwości** okna, typ nazwy symbolu następuje znak równości i całkowitą **identyfikator** polu, na przykład:

    ```
    IDC_EDITNAME=5100
    ```

   Nowa wartość są przechowywane w pliku nagłówkowym symboli podczas następnego zapisany projekt. Tylko nazwa symbolu pozostaje widoczna w polu Identyfikator i równości i wartości nie są wyświetlane po ich są weryfikowane.

## <a name="change-or-delete-symbols"></a>Zmień lub Usuń symbole

W [okno dialogowe symboli zasobów](../windows/resource-symbols-dialog-box.md), edytować lub usunąć istniejące symboli, które nie są już przypisane do zasobu lub obiektu.

### <a name="to-change-an-unassigned-symbol"></a>Aby zmienić nieprzypisanych symboli

1. W **nazwa** wybierz nieprzypisanych symboli, a wybierz **zmiany**.

1. Edytuj nazwę symbolu lub wartości w polach w **Zmień Symbol** okno dialogowe.

> [!NOTE]
> Aby zmienić symbol, który jest przypisany do zasobu lub obiektu, należy użyć edytora zasobów lub **właściwości** okna.

### <a name="to-delete-an-unassigned-unused-symbol"></a>Aby usunąć nieprzypisanych symboli (nieużywane)

W **symboli zasobów** okna dialogowego Wybierz symbol, który chcesz usunąć, a następnie wybierz **Usuń**.

> [!NOTE]
> Przed usunięciem nieużywane symboli w pliku zasobów, upewnij się, że nie jest on używany gdzie indziej w programie lub plików zasobów znajdujących się w czasie kompilacji.

## <a name="include-symbols"></a>Dołączać symbole

Środowisko projektowe odczytuje plik zasobów utworzony przez inną aplikację po raz pierwszy oznacza wszystkie pliki nagłówkowe dołączone jako tylko do odczytu. Chociaż można użyć [zasób zawiera okno dialogowe](../windows/resource-includes-dialog-box.md) można dodać dodatkowe symboli tylko do odczytu plików nagłówkowych.

Jest jednym z powodów warto używać definicje symboli tylko do odczytu dla plików symboli, które mają być udostępnianie dla kilku projektów.

Umożliwia także pliki symboli uwzględnione Jeśli masz istniejące zasoby dzięki definicje symboli, używające wyrażenia zamiast prostych liczb całkowitych do definiowania wartości symbolu. Na przykład:

```cpp
#define   IDC_CONTROL1 2100
#define   IDC_CONTROL2 (IDC_CONTROL1+1)
```

Środowisko zostanie poprawnie interpretować te symbole obliczane tak długo, jak:

- Symbole obliczane są umieszczane w pliku symboli tylko do odczytu.

- Plik zasobów zawiera zasoby, do których te symbole obliczane są już przypisane.

- Oczekiwano wyrażenia liczbowego.

> [!NOTE]
> Jeśli oczekiwany jest ciąg lub wyrażenie numeryczne, wyrażenie nie jest oceniany.

### <a name="to-include-shared-read-only-symbols-in-your-resource-file"></a>Aby uwzględnić symbole udostępnione (tylko do odczytu) w pliku zasobów

1. W [widok zasobów](how-to-create-a-resource-script-file.md#create-resources), kliknij prawym przyciskiem myszy użytkownika *.rc* plik i wybierz [zasób zawiera](../windows/resource-includes-dialog-box.md).

1. W **dyrektywy symboli tylko do odczytu** , używaj `#include` dyrektywy kompilatora, aby określić plik, którego symbole tylko do odczytu, które mają być przechowywane.

   Nie wywołuj pliku `Resource.h`, ponieważ jest to, nazwa_pliku zwykle używane przez plik nagłówka symbolu głównego.

   > [!NOTE]
   > Wpisz w **dyrektywy symboli tylko do odczytu** pola znajdują się w pliku zasobów, dokładnie tak, jak możesz wpisać. Upewnij się, w jakiej został wpisany nie zawiera błędów pisowni lub nieprawidłowa składnia.

   Użyj **dyrektywy symboli tylko do odczytu** pole, aby uwzględnić pliki przy użyciu tylko definicje symbolu. Nie zawierają definicje zasobów, inne zduplikowane definicje zostaną utworzone, gdy plik jest zapisywany.

1. W pliku, który określiłeś, należy umieścić symbole.

   Symbole w plików znajdujących się w ten sposób są obliczane zawsze przy otwieraniu Twojego pliku zasobu, ale nie są zastępowane na dysku po zapisaniu pliku.

1. Kliknij przycisk **OK**.

### <a name="to-change-the-name-of-the-resource-symbol-header-file"></a>Aby zmienić nazwę pliku nagłówkowego symboli zasobów

1. W [widok zasobów](how-to-create-a-resource-script-file.md#create-resources), kliknij prawym przyciskiem myszy użytkownika *.rc* pliku, a następnie wybierz [zasób zawiera](../windows/resource-includes-dialog-box.md).

1. W **plik nagłówka symbolu** wpisz nową nazwę dla pliku dyrektywy include.

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz także

[Identyfikatory zasobów (symbolom)](../windows/symbols-resource-identifiers.md)<br/>
[Instrukcje: Tworzenie symboli](../windows/creating-new-symbols.md)<br/>
[Wstępnie zdefiniowane symbole identyfikatorów](../windows/predefined-symbol-ids.md)<br/>