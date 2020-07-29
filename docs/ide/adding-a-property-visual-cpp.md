---
title: Dodawanie właściwości
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
ms.openlocfilehash: 125d7272b5b9fb0f656ba0621667885026e152fb
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228677"
---
# <a name="add-a-property"></a>Dodawanie właściwości

Aby dodać metodę do interfejsu w projekcie, można użyć [Kreatora dodawania właściwości](#names-add-property-wizard) .

**Aby dodać właściwość do obiektu:**

1. W [Widok klasy](/visualstudio/ide/viewing-the-structure-of-code)kliknij prawym przyciskiem myszy nazwę interfejsu, do którego chcesz dodać właściwość.

   > [!NOTE]
   > Możesz również dodać właściwości do dispinterfaces, które, chyba że projekt jest przypisany do atrybutu, są zagnieżdżone w węźle biblioteki.

1. Z menu skrótów wybierz polecenie **Dodaj**, a następnie wybierz polecenie **Dodaj właściwość**.

1. W [Kreatorze dodawania właściwości](#names-add-property-wizard)podaj informacje, aby utworzyć właściwość.

1. Określ wszystkie ustawienia języka definicji interfejsu (IDL) dla właściwości na stronie [atrybuty IDL](#idl-attributes-add-property-wizard) kreatora.

1. Wybierz pozycję **Zakończ** , aby dodać właściwość.

`Get`Metody i `Put` właściwości są wyświetlane jako dwie ikony w widok klasy w obszarze interfejsu, w którym jest zdefiniowany. Możesz dwukrotnie kliknąć każdą ikonę, aby wyświetlić deklarację właściwości w pliku IDL.

- W przypadku interfejsów ATL `Get` funkcje i `Put` są dodawane do pliku. cpp, a odwołania do tych funkcji są dodawane do pliku h.

- W przypadku dispinterfaces MFC, jeśli wybierzesz **zmienną członkowską** jako typ implementacji, Metoda i zmienna są dodawane do klasy implementującej ją. W przypadku wybrania **metod get/set** jako typu implementacji dwie metody są dodawane do klasy implementującej ją.

## <a name="in-this-section"></a>W tej sekcji

- [Nazwy, Kreator dodawania właściwości](#names-add-property-wizard)
- [Atrybuty IDL, Kreator dodawania właściwości](#idl-attributes-add-property-wizard)
- [Właściwości podstawowe](#stock-properties)

## <a name="names-add-property-wizard"></a>Nazwy, Kreator dodawania właściwości

Użyj tego kreatora, aby dodać właściwość do interfejsu.

- **Typ właściwości**

  Ustawia typ dodawanej właściwości. W przypadku biblioteki MFC dispinterfaces podaj własny typ lub wybierz pozycję ze wstępnie zdefiniowanej listy. Jeśli podano implementację giełdową właściwości, **Typ właściwości** jest ustawiany na typ magazynu i jest niedostępny do zmiany.

- **Nazwa właściwości**

  Ustawia nazwę właściwości. W przypadku MFC dispinterfaces skojarzonych z kontrolkami ActiveX można podać własną nazwę lub wybrać nazwę właściwości giełdowej ze wstępnie zdefiniowanej listy. Jeśli podano własną nazwę właściwości, typ implementacji **zapasowej** jest niedostępny. Zobacz [Właściwości giełdowe](#stock-properties) , aby uzyskać opis właściwości na liście.

  |Typ interfejsu|Opis|
  |--------------------|-----------------|
  |Interfejs ATL Dual Interface, niestandardowy interfejs i lokalny|Podaj nazwę właściwości.|
  |MFC dispinterface, Kontrolka ActiveX MFC dispinterface|Podaj nazwę właściwości lub wybierz z listy Właściwość giełdową. Jeśli wybierzesz właściwość z listy, odpowiednia wartość zostanie wyświetlona w polu **Typ właściwości** . Ten typ można zmienić, w zależności od dokonanego wyboru w obszarze **Typ implementacji**.|

- **Typ zwracany**

  Tylko interfejsy ATL. Ustawia zwracany typ dla właściwości. W przypadku podwójnych interfejsów `HRESULT` jest zawsze typem zwracanym, a to pole jest niedostępne. W przypadku interfejsów niestandardowych można wybrać typ zwracany z listy. `HRESULT`jest nadal zalecane, ponieważ zapewnia standardowy sposób zwracania błędów.

- **Nazwa zmiennej**

  Tylko MFC dispinterfaces. Dostępne tylko wtedy, gdy w obszarze **Typ implementacji**określono **zmienną członkowską** . Ustawia nazwę zmiennej członkowskiej, z którą skojarzona jest właściwość. Domyślnie nazwa zmiennej jest ustawiona na `m_` *PropertyName*. Można edytować tę nazwę.

- **Funkcja powiadomień**

  Tylko MFC dispinterfaces. Dostępne tylko wtedy, gdy w obszarze **Typ implementacji**określono **zmienną członkowską** . Ustawia nazwę funkcji powiadomień wywoływanej, jeśli właściwość zostanie zmieniona. Domyślnie nazwa funkcji powiadomień jest ustawiona na `On` *PropertyName* `Changed` . Można edytować tę nazwę.

- **Get, funkcja**

  Dla MFC dispinterfaces. Dostępne tylko w przypadku określenia **metod get/set** w obszarze **Typ implementacji**. Ustawia nazwę funkcji, aby pobrać właściwość. Domyślnie nazwa `Get` funkcji jest ustawiona na `Get` *PropertyName*. Można edytować tę nazwę. W przypadku usunięcia nazwy funkcja [GetNotSupported](../mfc/reference/colecontrol-class.md#getnotsupported) zostanie wstawiona do mapy wysyłania interfejsu. Funkcja `Get` *PropertyName* określa, że właściwość jest odczytywana.

- **Set — funkcja**

  Tylko MFC dispinterfaces. Dostępne tylko w przypadku określenia **metod get/set** w obszarze **Typ implementacji**. Ustawia nazwę funkcji, aby ustawić właściwość. Domyślnie nazwa `Set` funkcji jest ustawiona na `Set` *PropertyName*. Można edytować tę nazwę. W przypadku usunięcia nazwy funkcja [SetNotSupported](../mfc/reference/colecontrol-class.md#setnotsupported) zostanie wstawiona do mapy wysyłania interfejsu. Funkcja `Set` *PropertyName* określa, że właściwość jest zapisywalna.

- **Typ implementacji**

  Tylko MFC dispinterfaces. Określa sposób implementacji dodawanej właściwości.

  |Typ implementacji|Opis|
  |-------------------------|-----------------|
  |**Stanu**|Określa implementację giełdową właściwości wybranej w polu **Nazwa właściwości**. Domyślnie. Aby uzyskać więcej informacji, zobacz [Właściwości giełdowe](#stock-properties).<br /><br /> W przypadku określenia **akcji**, **Typ właściwości**, **Typ parametru**i **Nazwa parametru** są wygaszone.|
  |**Zmienna członkowska**|Określa, że właściwość jest dodawana jako zmienna członkowska. Możesz dodać właściwości niestandardowe lub większość właściwości podstawowych jako zmienne składowe. Nie można określić **zmiennej składowej** dla `Caption` `hWnd` właściwości, i `Text` .<br /><br /> Zawiera nazwy domyślne w obszarze **Nazwa zmiennej** i **Funkcja powiadomień**. Można edytować tę nazwę.|
  |**Metody get/set**|Określa, że właściwość jest domyślnie dodawana jako `Get` Funkcja *PropertyName* i `Set` *PropertyName* . Te nazwy są wyświetlane w obszarze **Pobierz funkcję** i **Ustaw funkcję**.<br /><br /> Można zmienić domyślny **Typ właściwości**, który przekazuje wartość funkcji get. Można określić parametry dla `Get` `Set` funkcji i.|

- **Get, funkcja**

  Dla interfejsów ATL. Ustawia właściwość jako czytelną; oznacza to, że tworzy `Get` metodę pobierania tej właściwości z obiektu. Wybierz pozycję **Get**, **Put**lub oba.

- **Put — funkcja**

  Tylko interfejsy ATL. Ustawia właściwość do zapisu; oznacza to, że tworzy `Put` metodę ustawiania lub "umieszczania" tej właściwości obiektu. Wybierz pozycję **Get**, **Put**lub oba. W przypadku wybrania tej opcji można wybrać jeden z następujących dwóch sposobów implementacji metody:

  |Opcja|Opis|
  |------------|-----------------|
  |**PropPut**|Funkcja [propput](../windows/propput.md) zwraca kopię obiektu. Jest to domyślny i najbardziej typowy sposób na zapisanie właściwości.|
  |**PropPutRef**|Funkcja [PropPutRef](../windows/propputref.md) zwraca odwołanie do obiektu, zamiast zwracać kopię samego obiektu. Należy rozważyć użycie tej opcji dla obiektów, takich jak duże struktury lub tablice, które mogą mieć obciążenie inicjalizacją.|

- **Atrybuty parametru**

  Tylko interfejsy ATL. Określa, czy parametr określony przez **parametr name** ma wartość `in` , `out` , Both lub None.

  |Opcja|Opis|
  |------------|-----------------|
  |`in`|Wskazuje, że parametr jest przesyłany z procedury wywołującej do procedury wywoływanej.|
  |`out`|Wskazuje, że parametr wskaźnika jest zwracany z wywoływanej procedury do procedury wywołującej (z serwera do klienta).|

- **Typ parametru**

  Ustawia typ danych parametru. Wybierz typ z listy.

- **Nazwa parametru**

  Ustawia nazwę parametru, który jest dodawany do właściwości, jeśli właściwość ma parametry. Po wybraniu opcji **Dodaj**Nazwa parametru zostanie wyświetlona na **liście parametrów**.

- **Lista parametrów**

  Wyświetla listę atrybutów, które mają zostać dodane do właściwości. Każdy element na liście składa się z nazwy parametru, typu parametru i atrybutów. Użyj **Dodaj** i **Usuń** , aby zaktualizować listę.

- **Dodaj**

  Dodaje parametr określony w polu **Nazwa parametru** i **Typ parametru** do **listy parametrów**. Wybierz pozycję **Dodaj** , aby dodać parametr do listy.

- **Usuń**

  Usuwa parametr wybrany na **liście parametrów**.

- **Właściwość domyślna**

  Tylko MFC dispinterface. Ustawia tę właściwość jako domyślną dla interfejsu. Interfejs może mieć tylko jedną właściwość domyślną; Po określeniu właściwości domyślnej dla wszystkich innych właściwości dodawanych do interfejsu to pole jest niedostępne.

## <a name="idl-attributes-add-property-wizard"></a>Atrybuty IDL, Kreator dodawania właściwości

Użyj tej strony Kreatora dodawania właściwości, aby określić ustawienia języka definicji interfejsu (IDL) dla właściwości.

- `id`

  Ustawia identyfikator liczbowy, który identyfikuje właściwość. Ta opcja jest niedostępna dla właściwości interfejsów niestandardowych. Zobacz [Identyfikator](/windows/win32/Midl/id) w *odwołaniu MIDL*.

- `helpcontext`

  Określa identyfikator kontekstu, który umożliwia użytkownikowi wyświetlanie informacji o tej właściwości w pliku pomocy. Zobacz [atrybut HelpContext](/windows/win32/Midl/helpcontext) w *dokumentacji MIDL*.

- `helpstring`

  Określa ciąg znaków, który jest używany do opisania elementu, do którego ma zastosowanie. Domyślnie jest ono ustawione na **`property`** &nbsp; * &nbsp; nazwę właściwości*. Zobacz [HelpString](/windows/win32/Midl/helpstring) w *dokumentacji MIDL*.

### <a name="other-options"></a>Inne opcje

Nie wszystkie opcje są dostępne dla wszystkich typów właściwości.

|Opcja|Opis|
|------------|-----------------|
|`bindable`|Wskazuje, że właściwość obsługuje powiązanie danych. Zobacz [powiązanie](/windows/win32/Midl/bindable) z *odwołaniem MIDL*. Dla implementacji giełdowej właściwości ta opcja jest domyślnie ustawiana i nie można jej zmienić.|
|`defaultbind`|Wskazuje, że ta pojedyncza, możliwa do powiązania Właściwość najlepiej reprezentuje obiekt. Zobacz [defaultbind](/windows/win32/Midl/defaultbind) w *dokumentacji MIDL*.|
|`displaybind`|Wskazuje, że ta właściwość powinna być wyświetlana użytkownikowi jako możliwy do powiązania. Zobacz [displaybind](/windows/win32/Midl/displaybind) w *dokumentacji MIDL*.|
|`immediatebind`|Wskazuje, że baza danych zostanie natychmiast powiadomiona o wszystkich zmianach właściwości obiektu powiązanego z danymi. Zobacz [immediatebind](/windows/win32/Midl/immediatebind) w *dokumentacji MIDL*.|
|`defaultcollelem`|Wskazuje, że właściwość jest funkcją dostępu dla elementu kolekcji domyślnej. Zobacz [defaultcollelem](/windows/win32/Midl/defaultcollelem) w *dokumentacji MIDL*.|
|`nonbrowsable`|Znaczniki elementu członkowskiego interfejsu lub dispinterface, który nie powinien być wyświetlany w przeglądarce właściwości. Zobacz [nonbrowsable](/windows/win32/Midl/nonbrowsable) w *dokumentacji MIDL*.|
|`requestedit`|Wskazuje, że właściwość obsługuje `OnRequestEdit` powiadomienie. Zobacz [requestedit](/windows/win32/Midl/requestedit) w *dokumentacji MIDL*. Dla implementacji giełdowej właściwości ta opcja jest domyślnie ustawiana i nie można jej zmienić.|
|`source`|Wskazuje, że element członkowski właściwości jest źródłem zdarzeń. Zobacz [Źródło](/windows/win32/Midl/source) w *MIDL Reference*.|
|`hidden`|Wskazuje, że właściwość istnieje, ale nie powinna być wyświetlana w przeglądarce zorientowanej na użytkownika. Zobacz [ukryty](/windows/win32/Midl/hidden) w *odwołaniu MIDL*.|
|`restricted`|Określa, że właściwość nie może być wywoływana arbitralnie. Zobacz [ograniczony](/windows/win32/Midl/restricted) w *MIDL Reference*.|
|`local`|Określa kompilatorowi MIDL, że właściwość nie jest zdalna. Zobacz [lokalne](/windows/win32/Midl/local) w *MIDL Reference*.|

## <a name="stock-properties"></a>Właściwości podstawowe

Jeśli dodajesz właściwość do dispinterface MFC przy użyciu [Kreatora dodawania właściwości](#idl-attributes-add-property-wizard), możesz wybrać Właściwość giełdową z listy **Nazwa właściwości** na stronie [nazwy](../ide/names-add-property-wizard.md) kreatora. Właściwości są następujące:

|Nazwa właściwości|Opis|
|-------------------|-----------------|
|`Appearance`|Zwraca lub ustawia wartość określającą wygląd formantu. Właściwość kontrolki `Appearance` może zawierać lub pominąć trójwymiarowe efekty wyświetlania. Ta właściwość jest otaczającą właściwością odczytu/zapisu.|
|`BackColor`|Zwraca lub ustawia właściwość otoczenia kontrolki `BackColor` na kolor palety (RGB) lub wstępnie zdefiniowany kolor systemu. Domyślnie jego wartość odnosi się do koloru pierwszego planu kontenera formantu. Ta właściwość jest otaczającą właściwością odczytu/zapisu.|
|`BorderStyle`|Zwraca lub ustawia styl obramowania kontrolki. Ta właściwość jest właściwością odczytu/zapisu.|
|`Caption`|Zwraca lub ustawia właściwość kontrolki `Caption` . Podpis jest tytułem okna. `Caption`nie ma typu implementacji **zmiennej składowej** .|
|`Enabled`|Zwraca lub ustawia właściwość kontrolki `Enabled` . Włączona kontrola może odpowiadać na zdarzenia generowane przez użytkownika.|
|`Font`|Zwraca lub ustawia otaczającą czcionkę formantu. Wartość null, Jeśli kontrolka nie ma czcionki.|
|`ForeColor`|Zwraca lub ustawia właściwość otoczenia kontrolki `ForeColor` .|
|`hWnd`|Zwraca lub ustawia właściwość kontrolki `hWnd` . `hWnd`nie ma typu implementacji **zmiennej składowej** .|
|`ReadyState`|Zwraca lub ustawia właściwość kontrolki `ReadyState` . Kontrolka może być niezainicjowana, zainicjowana, załadowana, interaktywna lub ukończona. Aby uzyskać więcej informacji, zobacz [READYSTATE](/previous-versions/aa768362\(v=vs.85\)) w *zestawie Internet SDK*.|
|`Text`|Zwraca lub ustawia tekst zawarty w kontrolce. `Text`nie ma typu implementacji **zmiennej składowej** .|
