---
title: Dodaj właściwość
ms.date: 11/09/2018
f1_keywords:
- vc.codewiz.prop.overview
- vc.codewiz.prop.idlattributes
helpviewer_keywords:
- interfaces, adding properties
- properties [C++], adding to interfaces
- names, add property wizard
- IDL attributes, add property wizard
- stock properties, about stock properties
- stock properties
ms.assetid: 37bd4db7-efd3-4faa-87ad-64902ed16a36
ms.openlocfilehash: 79938cb5c762292c5e1802832477c3a568ae2fdb
ms.sourcegitcommit: ecf274bcfe3a977c48745aaa243e5e731f1fdc5f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66504473"
---
# <a name="add-a-property"></a>Dodaj właściwość

Możesz użyć [Kreator dodawania właściwości](#names-add-property-wizard) Aby dodać metodę do interfejsu w projekcie.

**Aby dodać właściwość do obiektu:**

1. W [Widok klas](/visualstudio/ide/viewing-the-structure-of-code), kliknij prawym przyciskiem myszy nazwę interfejsu, do którego chcesz dodać właściwość.

   > [!NOTE]
   > Można również dodać właściwości do dispinterfaces, który, chyba że projekt jest przypisane, są zagnieżdżone w obrębie węzła biblioteki.

1. Z menu skrótów wybierz polecenie **Dodaj**, a następnie wybierz **Dodaj właściwość**.

1. W [Kreator dodawania właściwości](#names-add-property-wizard), podaj informacje, aby utworzyć właściwość.

1. Określ jakiekolwiek ustawienia interfejsu definicja języka (IDL) dla właściwości w [atrybuty IDL](#idl-attributes-add-property-wizard) strony kreatora.

1. Wybierz **Zakończ** można dodać właściwości.

`Get` i `Put` metody, właściwości są wyświetlane jako dwie ikony w widoku klas w obszarze interfejs, w którym jest zdefiniowana. Możesz kliknąć dwukrotnie albo ikonę, aby wyświetlić deklaracja właściwości w pliku .idl.

- W przypadku interfejsów ATL `Get` i `Put` funkcje są dodawane do pliku .cpp i odwołania do tych funkcji są dodawane do pliku .h.

- Dla dispinterfaces MFC, jeśli zostanie wybrana **zmiennej składowej** jako typ implementacji metody i zmienna są dodawane do klasy, która implementuje go. Jeśli wybierzesz **metod Get/Set** jako typ implementacji dwie metody są dodawane do klasy, która implementuje go.

## <a name="in-this-section"></a>W tej sekcji

- [Nazwy, Kreator dodawania właściwości](#names-add-property-wizard)
- [Atrybuty IDL, Kreator dodawania właściwości](#idl-attributes-add-property-wizard)
- [Właściwości podstawowe](#stock-properties)

## <a name="names-add-property-wizard"></a>Nazwy, Kreator dodawania właściwości

Użyj tego kreatora, aby dodać właściwość do interfejsu.

- **Typ właściwości**

  Ustawia typ właściwości, które dodajesz. Dla dispinterfaces MFC Podaj swój własny typ, lub wybierz z listy wstępnie zdefiniowanych. Jeśli podasz podstawowego wdrożenia właściwość **typ właściwości** ustawiono typu podstawowego, a jest niedostępna w przypadku zmiany.

- **Nazwa właściwości**

  Ustawia nazwę właściwości. Dispinterfaces MFC związane z kontrolkami ActiveX możesz podać własną nazwę lub nazwy podstawowe właściwości można wybrać z listy wstępnie zdefiniowanych. Jeśli podasz swoją własną nazwę właściwości **Stock** typ wdrożenia nie jest dostępny. Zobacz [podstawowy właściwości](#stock-properties) opis właściwości na liście.

  |Typ interfejsu|Opis|
  |--------------------|-----------------|
  |ATL podwójnego interfejsu, niestandardowego interfejsu i lokalne niestandardowy interfejs|Podaj nazwę właściwości.|
  |Dispinterface MFC, dispinterface kontrolki MFC ActiveX|Podaj nazwę właściwości lub wybierz właściwości podstawowych, z listy. Jeśli wybierzesz właściwość z listy odpowiednią wartość pojawia się w **typ właściwości** pola. Można zmienić tego typu, w zależności od wyboru w obszarze **typ implementacji**.|

- **Zwracany typ**

  Tylko ATL interfejsów. Ustawia typ zwrotny dla właściwości. Podwójne interfejsy `HRESULT` jest zawsze typem zwracanym, a to pole jest niedostępne. Dla interfejsów niestandardowych można wybrać typ zwracany z listy. `HRESULT` nadal zaleca się, ponieważ zawiera ono standardowy sposób zwracane błędy.

- **Nazwa zmiennej**

  Tylko dispinterfaces MFC. Dostępne tylko w przypadku określenia **zmiennej składowej** w obszarze **typ implementacji**. Określa nazwę zmiennej składowej, z którą właściwość jest skojarzony. Domyślnie, nazwa zmiennej jest równa `m_` *PropertyName*. Możesz edytować tę nazwę.

- **Funkcja powiadomień**

  Tylko dispinterfaces MFC. Dostępne tylko w przypadku określenia **zmiennej składowej** w obszarze **typ implementacji**. Ustawia nazwę powiadomień funkcji o nazwie, jeśli zmiany właściwości. Domyślnie, nazwa funkcji powiadomień jest równa `On` *PropertyName*`Changed`. Możesz edytować tę nazwę.

- **Funkcja Get**

  Aby uzyskać MFC dispinterfaces. Dostępne tylko w przypadku określenia **metod Get/Set** w obszarze **typ implementacji**. Ustawia nazwę funkcji do pobrania właściwości. Domyślnie nazwa `Get` funkcja jest ustawiona na `Get` *PropertyName*. Możesz edytować tę nazwę. Jeśli usuniesz nazwę funkcji [getnotsupported —](../mfc/reference/colecontrol-class.md#getnotsupported) są wstawiane do mapy wysyłania interfejsu. `Get` *PropertyName* funkcji określa, że właściwość do odczytu.

- **Funkcja set**

  Tylko dispinterfaces MFC. Dostępne tylko w przypadku określenia **metod Get/Set** w obszarze **typ implementacji**. Ustawia nazwę funkcji, należy ustawić właściwości. Domyślnie nazwa `Set` funkcja jest ustawiona na `Set` *PropertyName*. Możesz edytować tę nazwę. Jeśli usuniesz nazwę funkcji [setnotsupported —](../mfc/reference/colecontrol-class.md#setnotsupported) są wstawiane do mapy wysyłania interfejsu. `Set` *PropertyName* funkcji określa, czy właściwość jest zapisywalna.

- **Typ implementacji**

  Tylko dispinterfaces MFC. Określa, jak implementować właściwość, którą dodajesz.

  |Typ implementacji|Opis|
  |-------------------------|-----------------|
  |**Zapasów**|Określa podstawowe implementacji właściwości wybranego w **nazwa właściwości**. Domyślnie. Aby uzyskać więcej informacji, zobacz [podstawowy właściwości](#stock-properties).<br /><br /> Jeśli określisz **Stock**, następnie **typ właściwości**, **typ parametru**, i **Nazwa parametru** są wygaszone.|
  |**Zmienna składowa**|Określa, że właściwość została dodana jako zmienną składową. Można dodać właściwości niestandardowe lub większość właściwości podstawowe, jako zmienne Członkowskie. Nie można określić **zmiennej składowej** dla `Caption`, `hWnd`, i `Text` właściwości.<br /><br /> Udostępnia domyślne nazwy w obszarze **nazwa zmiennej** i **funkcję powiadomień**. Możesz edytować tę nazwę.|
  |**Metody GET/Set**|Określa właściwość jest dodawany jako `Get` *PropertyName* i `Set` *PropertyName* funkcje domyślne. Te nazwy są wyświetlane w obszarze **Get — funkcja** i **funkcja Set**.<br /><br /> Domyślne można zmienić **typ właściwości**, która przekazuje wartość dla funkcji Get. Można określić parametry `Get` i `Set` funkcji.|

- **Funkcja Get**

  ATL interfejsów. Ustawia właściwość jako do odczytu; oznacza to, tworzy `Get` metodę pobierania tej właściwości z obiektu. Wybierz **uzyskać**, **umieścić**, lub obu.

- **Umieść — funkcja**

  Tylko ATL interfejsów. Ustawia właściwość zapisywalnej; oznacza to, tworzy `Put` metoda ustawienie lub "wprowadzenie", ta właściwość obiektu. Wybierz **uzyskać**, **umieścić**, lub obu. Jeśli wybierzesz tę opcję, można wybrać z dwóch poniższych sposobów, aby wdrożyć metodę:

  |Opcja|Opis|
  |------------|-----------------|
  |**PropPut**|[PropPut](../windows/propput.md) funkcja zwraca kopię obiektu. Jest to domyślny i najbardziej popularny sposób, aby ustawić właściwość jako zapisu.|
  |**PropPutRef**|[PropPutRef](../windows/propputref.md) funkcja zwraca odwołanie do obiektu, a nie zwraca kopię obiektu. Rozważ użycie tej opcji dla obiektów, takich jak duże strukturami lub tablic, które mogą mieć obciążenie inicjowania.|

- **Atrybuty parametru**

  Tylko ATL interfejsów. Określa, czy parametr jest określony przez **Nazwa parametru** jest `in`, `out`, zarówno lub Brak.

  |Opcja|Opis|
  |------------|-----------------|
  |`in`|Wskazuje, że parametr jest przekazywany z procedury wywołującej do procedury wywoływanej.|
  |`out`|Wskazuje, że parametr wskaźnika jest zwracana z procedury wywoływanej do procedury wywołującej (z serwera do klienta).|

- **Typ parametru**

  Ustawia typ danych parametru. Wybierz typ z listy.

- **Nazwa parametru**

  Określa nazwę parametru dodawanego dla właściwości, jeśli właściwość ma następujące parametry. Po wybraniu **Dodaj**, nazwa parametru jest wyświetlana w **listy parametrów**.

- **Lista parametrów**

  Wyświetla listę atrybutów, które mają zostać dodane do właściwości. Każdy element na liście składa się z nazwy parametru typu parametru i atrybutów. Użyj **Dodaj** i **Usuń** można zaktualizować listy.

- **Add**

  Dodaje parametr należy określić w **Nazwa parametru** i **typ parametru** do **listy parametrów**. Wybierz **Dodaj** Aby dodać parametr do listy.

- **Usuń**

  Usuwa parametr w **listy parametrów**.

- **Domyślna właściwość**

  Tylko dispinterface MFC. Ustawia tę właściwość jako wartość domyślna dla interfejsu. Interfejs może mieć tylko jedną domyślną właściwości Po określeniu domyślnej właściwości, dla innych właściwości, jeśli są dodawane do interfejsu, to pole jest niedostępne.

## <a name="idl-attributes-add-property-wizard"></a>Atrybuty IDL, Kreator dodawania właściwości

Ta strona kreatora dodawania właściwości umożliwia Określ jakiekolwiek ustawienia interfejsu definicja języka (IDL) dla właściwości.

- `id`

  Określa numeryczny identyfikator, który identyfikuje właściwość. Ta opcja jest niedostępna dla właściwości niestandardowych interfejsów. Zobacz [identyfikator](/windows/desktop/Midl/id) w *odwołania MIDL*.

- `helpcontext`

  Określa identyfikator kontekstu, który pozwala użytkownikowi oglądać informacje o tej właściwości w pliku pomocy. Zobacz [helpcontext —](/windows/desktop/Midl/helpcontext) w *odwołania MIDL*.

- `helpstring`

  Określa ciąg znaków, który jest używany do opisania elementu, do której jest stosowany. Domyślnie jest ustawiona `property` &nbsp; *właściwość&nbsp;nazwa*. Zobacz [HelpString —](/windows/desktop/Midl/helpstring) w *odwołania MIDL*.

### <a name="other-options"></a>Inne opcje

Nie wszystkie opcje są dostępne dla wszystkich typów właściwości.

|Opcja|Opis|
|------------|-----------------|
|`bindable`|Wskazuje, że właściwość obsługuje powiązanie danych. Zobacz [możliwej do wiązania](/windows/desktop/Midl/bindable) w *odwołania MIDL*. Wykonania akcji właściwość ta opcja jest ustawiana domyślnie i można zmienić.|
|`defaultbind`|Wskazuje, czy ta właściwość pojedynczy, które można powiązać najlepiej reprezentuje obiekt. Zobacz [defaultbind —](/windows/desktop/Midl/defaultbind) w *odwołania MIDL*.|
|`displaybind`|Wskazuje, że ta właściwość powinna być wyświetlana użytkownikowi jak możliwa do powiązania. Zobacz [displaybind —](/windows/desktop/Midl/displaybind) w *odwołania MIDL*.|
|`immediatebind`|Wskazuje, że baza danych zostanie niezwłocznie powiadomiona o wszystkich zmianach tej właściwości obiektów powiązanych z danymi. Zobacz [immediatebind —](/windows/desktop/Midl/immediatebind) w *odwołania MIDL*.|
|`defaultcollelem`|Wskazuje, że właściwość jest funkcję dostępu do elementu domyślnej kolekcji. Zobacz [defaultcollelem —](/windows/desktop/Midl/defaultcollelem) w *odwołania MIDL*.|
|`nonbrowsable`|Tagi elementu członkowskiego interfejsu lub dispinterface nie powinien być wyświetlany w przeglądarce właściwości. Zobacz [nonbrowsable —](/windows/desktop/Midl/nonbrowsable) w *odwołania MIDL*.|
|`requestedit`|Wskazuje, że właściwość obsługuje `OnRequestEdit` powiadomień. Zobacz [requestedit —](/windows/desktop/Midl/requestedit) w *odwołania MIDL*. Wykonania akcji właściwość ta opcja jest ustawiana domyślnie i można zmienić.|
|`source`|Wskazuje, że jest członkiem właściwość jest źródłem zdarzeń. Zobacz [źródła](/windows/desktop/Midl/source) w *odwołania MIDL*.|
|`hidden`|Wskazuje, że właściwość istnieje, ale nie powinien być wyświetlany w przeglądarce zorientowanej na użytkownika. Zobacz [ukryte](/windows/desktop/Midl/hidden) w *odwołania MIDL*.|
|`restricted`|Określa, że właściwość nie może być wywoływana arbitralnie. Zobacz [ograniczeniami](/windows/desktop/Midl/restricted) w *odwołania MIDL*.|
|`local`|Określa kompilatorowi MIDL, że właściwość nie jest zdalny. Zobacz [lokalnego](/windows/desktop/Midl/local) w *odwołania MIDL*.|

## <a name="stock-properties"></a>Właściwości podstawowe

Jeśli dodajesz właściwości dispinterface MFC za pomocą [Kreator dodawania właściwości](#idl-attributes-add-property-wizard), można wybrać właściwości podstawowych z **nazwa właściwości** listy w [nazwy](../ide/names-add-property-wizard.md) strony Kreator. Właściwości są następujące:

|Nazwa właściwości|Opis|
|-------------------|-----------------|
|`Appearance`|Zwraca lub ustawia wartość określającą, wygląd formantu. Kontrolki `Appearance` właściwości można uwzględnić lub pominąć efekty trójwymiarowych. Ta właściwość jest właściwością otoczenia odczytu/zapisu.|
|`BackColor`|Zwraca lub ustawia formantu otoczenia `BackColor` właściwość kolor z palety (RGB) lub kolor wstępnie zdefiniowanego. Domyślnie jej wartość odpowiada kolor pierwszego planu kontener formantu. Ta właściwość jest właściwością otoczenia odczytu/zapisu.|
|`BorderStyle`|Zwraca lub ustawia styl obramowania kontrolki. Ta właściwość jest właściwością odczytu/zapisu.|
|`Caption`|Zwraca lub ustawia formantu `Caption` właściwości. Podpis jest tytuł okna. `Caption` nie ma przypisanego **zmiennej składowej** typ implementacji.|
|`Enabled`|Zwraca lub ustawia formantu `Enabled` właściwości. Kontrolka w postaci włączone może odpowiadać na zdarzenia generowane przez użytkownika.|
|`Font`|Zwraca lub ustawia czcionkę otoczenia formantu. Wartość null, jeśli kontrolka ma nie czcionki.|
|`ForeColor`|Zwraca lub ustawia formantu otoczenia `ForeColor` właściwości.|
|`hWnd`|Zwraca lub ustawia formantu `hWnd` właściwości. `hWnd` nie ma przypisanego **zmiennej składowej** typ implementacji.|
|`ReadyState`|Zwraca lub ustawia formantu `ReadyState` właściwości. Formant może być niezainicjowanej, zainicjowane, ładowanie, interakcyjnego lub pełne. Aby uzyskać więcej informacji, zobacz [READYSTATE](/previous-versions//aa768362\(v=vs.85\)) w *Internet SDK*.|
|`Text`|Zwraca lub ustawia tekst zawarty w kontrolce. `Text` nie ma przypisanego **zmiennej składowej** typ implementacji.|
