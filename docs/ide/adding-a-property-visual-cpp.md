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
ms.openlocfilehash: 79b05fde362a44453aac45aa8dc269c9689ea8fc
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81751187"
---
# <a name="add-a-property"></a>Dodawanie właściwości

[Kreatora dodawania właściwości](#names-add-property-wizard) można użyć, aby dodać metodę do interfejsu w projekcie.

**Aby dodać właściwość do obiektu:**

1. W [widoku klasy](/visualstudio/ide/viewing-the-structure-of-code)kliknij prawym przyciskiem myszy nazwę interfejsu, do którego chcesz dodać właściwość.

   > [!NOTE]
   > Można również dodać właściwości do dispinterfaces, które, o ile projekt nie jest przypisany, są zagnieżdżone w węźle biblioteki.

1. Z menu skrótów wybierz polecenie **Dodaj**, a następnie wybierz pozycję **Dodaj właściwość**.

1. W [kreatorze dodawania właściwości](#names-add-property-wizard)podaj informacje, aby utworzyć właściwość.

1. Określ dowolne ustawienia języka definicji interfejsu (IDL) dla właściwości na stronie [atrybuty IDL](#idl-attributes-add-property-wizard) kreatora.

1. Wybierz **pozycję Zakończ,** aby dodać właściwość.

I `Get` `Put` metody właściwości są wyświetlane jako dwie ikony w widoku klasy, w interfejsie, w którym jest zdefiniowany. Można kliknąć dwukrotnie jedną z ikon, aby wyświetlić deklarację właściwości w pliku .idl.

- W przypadku interfejsów `Get` ATL i `Put` funkcje są dodawane do pliku .cpp, a odwołania do tych funkcji są dodawane do pliku .h.

- Dla MFC dispinterfaces, jeśli wybierzesz **Zmienna Elementu Członkowskiego** jako typ implementacji, metoda i zmienna są dodawane do klasy, która implementuje go. Jeśli wybierzesz **Get/Set metody** jako typ implementacji, dwie metody są dodawane do klasy, która implementuje go.

## <a name="in-this-section"></a>W tej sekcji

- [Nazwy, dodaj kreatora właściwości](#names-add-property-wizard)
- [Atrybuty IDL, kreator dodawania właściwości](#idl-attributes-add-property-wizard)
- [Nieruchomości magazynowe](#stock-properties)

## <a name="names-add-property-wizard"></a>Nazwy, dodaj kreatora właściwości

Ten kreator służy do dodawania właściwości do interfejsu.

- **Typ właściwości**

  Ustawia typ dodanej właściwości. W przypadku dispinterfaces MFC, podaj swój własny typ lub wybierz z listy wstępnie zdefiniowane. Jeśli podasz implementację zapasów właściwości, **Typ właściwości** jest ustawiony na typ magazynu i jest niedostępny do zmiany.

- **Nazwa właściwości**

  Ustawia nazwę właściwości. W przypadku dispinterfaces MFC skojarzonych z formantami ActiveX można podać własną nazwę lub nazwę właściwości magazynu z wstępnie zdefiniowanej listy. Jeśli podasz własną nazwę właściwości, typ implementacji **zapasów** jest niedostępny. Opis właściwości na liście można znaleźć w [właściwościach magazynowych.](#stock-properties)

  |Typ interfejsu|Opis|
  |--------------------|-----------------|
  |Podwójny interfejs ATL, interfejs niestandardowy i lokalny interfejs niestandardowy|Podaj nazwę właściwości.|
  |MFC dispinterface, MFC ActiveX sterowanie dispinterface|Podaj nazwę właściwości lub wybierz właściwość magazynową z listy. Jeśli wybierzesz właściwość z listy, odpowiednia wartość pojawi się w polu **Typ właściwości.** Można zmienić ten typ, w zależności od wyboru w obszarze **Typ implementacji**.|

- **Zwracany typ**

  Tylko interfejsy ATL. Ustawia typ zwracany dla właściwości. W przypadku dwóch `HRESULT` interfejsów jest zawsze typem zwracany, a to pole jest niedostępne. W przypadku interfejsów niestandardowych można wybrać typ zwracany z listy. `HRESULT`jest nadal zalecane, ponieważ zapewnia standardowy sposób zwracania błędów.

- **Nazwa zmiennej**

  MFC dispinterfaces tylko. Dostępne tylko wtedy, gdy określisz **zmienną elementu członkowskiego** w obszarze **Typ implementacji**. Ustawia nazwę zmiennej członkowskiej, z którą jest skojarzona właściwość. Domyślnie nazwa zmiennej jest `m_`ustawiona na *PropertyName*. Możesz edytować tę nazwę.

- **Funkcja powiadomień**

  MFC dispinterfaces tylko. Dostępne tylko wtedy, gdy określisz **zmienną elementu członkowskiego** w obszarze **Typ implementacji**. Ustawia nazwę funkcji powiadomień wywołanej, jeśli właściwość ulegnie zmianie. Domyślnie nazwa funkcji powiadomień jest `On` *ustawiona na PropertyName*`Changed`. Możesz edytować tę nazwę.

- **Get, funkcja**

  Dla MFC dispinterfaces. Dostępne tylko wtedy, gdy określisz **metody Get/Set** w obszarze **Typ implementacji**. Ustawia nazwę funkcji, aby uzyskać właściwość. Domyślnie nazwa funkcji `Get` jest ustawiona `Get`na *PropertyName*. Możesz edytować tę nazwę. Jeśli usuniesz nazwę, funkcja [GetNotSupported](../mfc/reference/colecontrol-class.md#getnotsupported) zostanie wstawiona do mapy wysyłki interfejsu. Funkcja `Get` *PropertyName* określa, że właściwość jest czytelna.

- **Ustaw funkcję**

  MFC dispinterfaces tylko. Dostępne tylko wtedy, gdy określisz **metody Get/Set** w obszarze **Typ implementacji**. Ustawia nazwę funkcji, aby ustawić właściwość. Domyślnie nazwa funkcji `Set` jest ustawiona `Set`na *PropertyName*. Możesz edytować tę nazwę. Jeśli usuniesz nazwę, funkcja [SetNotSupported](../mfc/reference/colecontrol-class.md#setnotsupported) zostanie wstawiona do mapy wysyłki interfejsu. Funkcja `Set` *PropertyName* określa, że właściwość jest zapisywalna.

- **Typ implementacji**

  MFC dispinterfaces tylko. Określa sposób implementacji właściwości, którą dodajesz.

  |Typ implementacji|Opis|
  |-------------------------|-----------------|
  |**Stock**|Określa implementację zapasów dla właściwości wybranej w **nazwa właściwości**. Domyślnie. Aby uzyskać więcej informacji, zobacz [właściwości zapasów](#stock-properties).<br /><br /> Jeśli określisz **stock**, następnie **typ właściwości,** **typ parametru**i **nazwa parametru** zostaną wyszarzone.|
  |**Zmienna elementu członkowskiego**|Określa, że właściwość jest dodawana jako zmienna elementu członkowskiego. Właściwości niestandardowe lub większość właściwości magazynowych można dodawać jako zmienne członkowskie. Nie można określić **zmiennej** `Caption` `hWnd`elementu `Text` członkowskiego dla , i właściwości.<br /><br /> Zawiera nazwy **domyślne** w obszarze Nazwa zmiennej i **Funkcja powiadomień**. Możesz edytować tę nazwę.|
  |**Metody get/set**|Określa, że właściwość `Get`jest domyślnie dodawana jako *propertyname* i `Set` *PropertyName.* Nazwy te są wyświetlane w obszarze **Pobierz funkcję** i **Ustaw funkcję**.<br /><br /> Można zmienić domyślny **typ właściwości**, który przekazuje wartość funkcji Pobierz. Można określić parametry `Get` `Set` i funkcje.|

- **Get, funkcja**

  Dla interfejsów ATL. Ustawia właściwość jako czytelną; oznacza to, że `Get` tworzy metodę pobierania tej właściwości z obiektu. Wybierz **pozycję Pobierz**, **Umieść**lub oba.

- **Umieść, funkcja**

  Tylko interfejsy ATL. Ustawia właściwość zapisywalną; oznacza to, że `Put` tworzy metodę ustawiania lub "oddanie", tej właściwości obiektu. Wybierz **pozycję Pobierz**, **Umieść**lub oba. Jeśli wybierzesz tę opcję, możesz wybrać jeden z następujących dwóch sposobów zaimplementowania metody:

  |Opcja|Opis|
  |------------|-----------------|
  |**Propput**|[PropPut](../windows/propput.md) Funkcja zwraca kopię obiektu. Jest to domyślny i najbardziej typowy sposób, aby właściwość zapisywalna.|
  |**PropPutRef (PropPutRef)**|[Funkcja PropPutRef](../windows/propputref.md) zwraca odwołanie do obiektu, zamiast zwracać kopię samego obiektu. Należy rozważyć użycie tej opcji dla obiektów, takich jak duże struktury lub tablice, które mogą mieć obciążenie inicjowania.|

- **Atrybuty parametru**

  Tylko interfejsy ATL. Określa, czy parametr określony `in`przez `out` **nazwę parametru** jest , oba lub żaden.

  |Opcja|Opis|
  |------------|-----------------|
  |`in`|Wskazuje, że parametr jest przekazywany z procedury wywołującej do procedury wywoływania.|
  |`out`|Wskazuje, że parametr wskaźnika jest zwracany z procedury wywoływania do procedury wywołującej (z serwera do klienta).|

- **Typ parametru**

  Ustawia typ danych parametru. Wybierz typ z listy.

- **Nazwa parametru**

  Ustawia nazwę parametru, który dodajesz dla właściwości, jeśli właściwość ma parametry. Po **wybraniu**opcji Dodaj nazwa parametru pojawi się na **liście parametrów**.

- **Lista parametrów**

  Wyświetla listę atrybutów, które mają zostać dodane do właściwości. Każdy element na liście składa się z nazwy parametru, typu parametru i atrybutów. Aby zaktualizować listę, użyj **funkcji Dodaj** i **usuń.**

- **Dodaj**

  Dodaje parametr określony w obszarze **Nazwa parametru** i **Typ parametru** do **listy Parametrów**. Wybierz **pozycję Dodaj,** aby dodać parametr do listy.

- **Usuń**

  Usuwa parametr wybrany na **liście parametrów**.

- **Właściwość domyślna**

  MFC dispinterface tylko. Ustawia tę właściwość jako domyślną dla interfejsu. Interfejs może mieć tylko jedną właściwość domyślną; po określeniu właściwości domyślnej dla innych właściwości dodawanych do interfejsu to pole jest niedostępne.

## <a name="idl-attributes-add-property-wizard"></a>Atrybuty IDL, kreator dodawania właściwości

Ta strona Kreatora dodawania właściwości służy do określania ustawień języka definicji interfejsu (IDL) dla właściwości.

- `id`

  Ustawia identyfikator numeryczny, który identyfikuje właściwość. Ta opcja nie jest dostępna dla właściwości interfejsów niestandardowych. Zobacz [id](/windows/win32/Midl/id) w *midl reference*.

- `helpcontext`

  Określa identyfikator kontekstu, który umożliwia użytkownikowi wyświetlanie informacji o tej właściwości w pliku Pomocy. Zobacz [helpcontext](/windows/win32/Midl/helpcontext) w *midl reference*.

- `helpstring`

  Określa ciąg znaków, który jest używany do opisania elementu, do którego ma zastosowanie. Domyślnie jest ustawiona `property` &nbsp;na *Nazwa właściwości&nbsp;*. Zobacz [helpstring](/windows/win32/Midl/helpstring) w *MIDL Reference*.

### <a name="other-options"></a>Inne opcje

Nie wszystkie opcje są dostępne dla wszystkich typów właściwości.

|Opcja|Opis|
|------------|-----------------|
|`bindable`|Wskazuje, że właściwość obsługuje powiązanie danych. Patrz [bindable](/windows/win32/Midl/bindable) w *MIDL Reference*. W przypadku implementacji właściwości zapasów ta opcja jest ustawiona domyślnie i jest niezmienna.|
|`defaultbind`|Wskazuje, że ta pojedyncza, powiązana właściwość najlepiej reprezentuje obiekt. Zobacz [defaultbind](/windows/win32/Midl/defaultbind) w *midl reference*.|
|`displaybind`|Wskazuje, że ta właściwość powinna być wyświetlana użytkownikowi jako możliwe do powiązania. Zobacz [displaybind](/windows/win32/Midl/displaybind) w *midl reference*.|
|`immediatebind`|Wskazuje, że baza danych zostanie natychmiast powiadomiona o wszystkich zmianach w tej właściwości obiektu powiązanego z danymi. Zobacz [immediatebind](/windows/win32/Midl/immediatebind) w *midl reference*.|
|`defaultcollelem`|Wskazuje, że właściwość jest funkcją akcesora dla elementu kolekcji domyślnej. Zobacz [defaultcollelem](/windows/win32/Midl/defaultcollelem) w *midl reference*.|
|`nonbrowsable`|Oznacza interfejs lub dispinterface element członkowski, który nie powinien być wyświetlany w przeglądarce właściwości. Zobacz, [że nie można brwi w](/windows/win32/Midl/nonbrowsable) *midl reference*.|
|`requestedit`|Wskazuje, że właściwość `OnRequestEdit` obsługuje powiadomienie. Patrz [requestedit](/windows/win32/Midl/requestedit) w *midl reference*. W przypadku implementacji właściwości zapasów ta opcja jest ustawiona domyślnie i jest niezmienna.|
|`source`|Wskazuje, że element członkowski właściwości jest źródłem zdarzeń. Zobacz [źródło](/windows/win32/Midl/source) w *midl reference*.|
|`hidden`|Wskazuje, że właściwość istnieje, ale nie powinny być wyświetlane w przeglądarce zorientowanej na użytkownika. Zobacz [ukryte](/windows/win32/Midl/hidden) w *MIDL Reference*.|
|`restricted`|Określa, że właściwości nie można wywołać dowolnie. Patrz [ograniczone](/windows/win32/Midl/restricted) w *midl reference*.|
|`local`|Określa kompilatora MIDL, że właściwość nie jest zdalna. Zobacz [lokalne](/windows/win32/Midl/local) w *midl reference*.|

## <a name="stock-properties"></a>Nieruchomości magazynowe

Jeśli dodajesz właściwość do dispinterface MFC za pomocą [kreatora dodawania właściwości,](#idl-attributes-add-property-wizard)możesz wybrać właściwość magazynu z listy **Nazwa właściwości** na stronie [Nazwy](../ide/names-add-property-wizard.md) kreatora. Właściwości są następujące:

|Nazwa właściwości|Opis|
|-------------------|-----------------|
|`Appearance`|Zwraca lub ustawia wartość, która określa wygląd formantu. `Appearance` Właściwości formantu można uwzględnić lub pominąć trójwymiarowe efekty wyświetlania. Ta właściwość jest właściwość odczytu/zapisu otoczenia.|
|`BackColor`|Zwraca lub ustawia właściwość `BackColor` otoczenia formantu na kolor palety (RGB) lub wstępnie zdefiniowany kolor systemu. Domyślnie jego wartość odpowiada kolor pierwszego planu kontenera formantu. Ta właściwość jest właściwość odczytu/zapisu otoczenia.|
|`BorderStyle`|Zwraca lub ustawia styl obramowania dla formantu. Ta właściwość jest właściwością odczytu/zapisu.|
|`Caption`|Zwraca lub ustawia `Caption` właściwość formantu. Podpis jest tytułem okna. `Caption`nie ma typu implementacji **zmiennej elementu członkowskiego.**|
|`Enabled`|Zwraca lub ustawia `Enabled` właściwość formantu. Włączona kontrolka może reagować na zdarzenia generowane przez użytkownika.|
|`Font`|Zwraca lub ustawia czcionkę otoczenia formantu. Null, jeśli formant nie ma czcionki.|
|`ForeColor`|Zwraca lub ustawia właściwość `ForeColor` otoczenia formantu.|
|`hWnd`|Zwraca lub ustawia `hWnd` właściwość formantu. `hWnd`nie ma typu implementacji **zmiennej elementu członkowskiego.**|
|`ReadyState`|Zwraca lub ustawia `ReadyState` właściwość formantu. Formant może być niezainicjowany, zainicjowany, załadowany, interaktywny lub ukończony. Aby uzyskać więcej informacji, zobacz [READYSTATE](/previous-versions/aa768362\(v=vs.85\)) w *internetowym SDK*.|
|`Text`|Zwraca lub ustawia tekst zawarty w formancie. `Text`nie ma typu implementacji **zmiennej elementu członkowskiego.**|
