---
title: Dodaj metodę
ms.date: 11/09/2018
f1_keywords:
- vc.codewiz.method.overview
- vc.codewiz.method.idlattrib
helpviewer_keywords:
- add method wizard [C++]
- methods [C++], adding
- methods [C++], adding using wizards
- IDL attributes, add method wizard
ms.assetid: 4ba4e45f-fa38-4d5e-af44-cbec0a7ab558
ms.openlocfilehash: 23fb05e633713016b1f6289f73a916502736af10
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/15/2018
ms.locfileid: "51692719"
---
# <a name="add-a-method"></a>Dodaj metodę

Możesz użyć [Kreator dodawania metody](#add-method-wizard) Aby dodać metodę do interfejsu w projekcie. Jeśli projekt zawiera klasę skojarzoną z interfejsem, Kreator zbyt modyfikuje klasy.

**Aby dodać metodę do obiektu:**

1. W **Widok klas**, rozwiń węzeł projektu, aby wyświetlić interfejsu, do którego chcesz dodać metody.

   > [!NOTE]
   > Metody można również dodać do dispinterfaces, który, chyba że projekt jest przypisane, znajdują się w węźle biblioteki.

1. Kliknij prawym przyciskiem myszy nazwę interfejsu.

1. W menu skrótów wybierz **Dodaj**, a następnie wybierz **Dodaj metodę**.

1. W Kreatorze dodawania metody Podaj informacje, aby utworzyć metodę.

1. Określ jakiekolwiek ustawienia języka definicji interfejsu dla tej metody w [atrybuty IDL](#idl-attributes-add-method-wizard) strony kreatora.

1. Wybierz **Zakończ** dodać metody.

## <a name="in-this-section"></a>W tej sekcji

- [Kreator dodawania metody](#add-method-wizard)
- [Atrybuty IDL, Kreator dodawania metody](#idl-attributes-add-method-wizard)

## <a name="add-method-wizard"></a>Kreator dodawania metody

Użyj tego kreatora, aby dodać metodę do interfejsu. W zależności od typu projektu lub typu interfejsu, do którego dodajesz metodę Kreator wyświetli inne opcje.

### <a name="names"></a>Nazwy

- **Zwracany typ**

  Typ danych zwracany przez metodę. `HRESULT` Zaleca się dla wszystkich typów interfejsu, ponieważ zawiera ono standardowy sposób zwracane błędy.

  |Typ interfejsu|Opis|
  |--------------------|-----------------|
  |Podwójnego interfejsu|`HRESULT`. Nie będzie zmieniana.|
  |Niestandardowy interfejs|`HRESULT`. Nie będzie zmieniana.|
  |Lokalny interfejs niestandardowe|Podaj swój własny typ zwracany lub wybierz z listy.|
  |Dispinterface|Podaj swój własny typ zwracany lub wybierz z listy.|
  |Dispinterface kontrolki MFC ActiveX|W przypadku zastosowania metody akcji, zwracany typ ma ustawioną wartość odpowiednią i można zmienić. Jeśli zostanie wybrana metoda z **nazwę metody** listy i wybierz **niestandardowe** w obszarze **wybierz typ metody**, wybierz typ zwracany z listy.|

- **Nazwa metody**

  Ustawia nazwę metody.

  |Typ interfejsu|Opis|
  |--------------------|-----------------|
  |ATL podwójnego interfejsu, niestandardowego interfejsu i lokalne niestandardowy interfejs|Podaj nazwę metody.|
  |MFC dispinterface|Podaj własną nazwę metody lub wybierz nazwę sugerowane metody z listy. Jeśli wybierzesz nazwę z listy odpowiednią wartość pojawia się w **zwracany typ** polu, a jego nie będzie zmieniana.|
  |Dispinterface kontrolki MFC ActiveX|Podaj własny lub wybrać jedną z metod standardowych [DoClick](../mfc/reference/colecontrol-class.md#doclick) i [Odśwież](../mfc/reference/colecontrol-class.md#refresh). Aby uzyskać więcej informacji, zobacz [kontrolki MFC ActiveX: dodawanie metod standardowych](../mfc/mfc-activex-controls-adding-stock-methods.md).|

- **Typ metody**

  Dostępne tylko dla kontrolek MFC ActiveX. Jeśli podasz nazwę metody w **nazwę metody** polu, zamiast wybierania metody na liście, to pole jest niedostępne.

  Po wybraniu jednej z metod w **nazwę metody** wybierz implementacji standardowych lub niestandardowych implementacji.

  |Typ metody|Opis|
  |-----------------|-----------------|
  |**Zapasów**|Domyślnie. Wstawia podstawowe implementacji metody, wybierz w **nazwę metody** listy. **Zwracany typ** można zmienić, jeśli zostanie wybrana **Stock**.|
  |**Custom**|Wstawia z implementacją wycinka Metoda wybrana w **nazwę metody** listy. W przypadku typów niestandardową metodę możesz podać swój własny typ zwracany lub możesz wybrać jeden z **zwracany typ** listy.|

- **Nazwa wewnętrzna**

  Dostępne tylko niestandardowych metod, dodane do dispinterface MFC. Ustawia nazwę używaną w Mapa wysyłania pliku nagłówka (.h) i plik implementacji (.cpp). Domyślnie ta nazwa jest taka sama jak **nazwę metody**. Możesz zmienić nazwę metody, jeśli pracujesz z dispinterface MFC lub tworzeniu niestandardową metodę dispinterface kontrolki MFC ActiveX.

  |Typ interfejsu|Opis|
  |--------------------|-----------------|
  |ATL podwójnego interfejsu, niestandardowego interfejsu i lokalne niestandardowy interfejs|Nie jest dostępna.|
  |MFC dispinterface|Domyślnie w nazwie metody. Można edytować nazwy wewnętrznej.|
  |Dispinterface kontrolki MFC ActiveX|Możesz ustawić nazwa wewnętrzna tylko w przypadku niestandardowych metod. Nazwa wewnętrzna nie należy używać metod standardowych.|

- **Atrybuty parametru**

  Ustawia wszelkie dodatkowe atrybuty dla parametru określonego w **Nazwa parametru**.

  |Atrybut parametru|Opis|Dozwolone kombinacje|
  |-------------------------|-----------------|--------------------------|
  |**W**|Wskazuje, że parametr jest przekazywany z procedury wywołującej do procedury wywoływanej.|`in` Tylko<br /><br /> `in` i `out`|
  |**limit**|Wskazuje, że parametr wskaźnika jest zwracana z procedury wywoływanej do procedury wywołującej (z serwera do klienta).|`out` Tylko<br /><br /> `in` i `out`<br /><br /> `out` i `retval`|
  |**retval**|Wskazuje, że parametr otrzymuje wartość zwrotną z elementu członkowskiego.|`retval` i `out`|

- **Typ parametru**

  Ustawia typ danych parametru. Wybierz typ z listy.

- **Nazwa parametru**

  Określa nazwę parametru, aby przechodzić przez metodę. Po wpisaniu nazwy, wybierz **Dodaj** ją dodać do listy parametrów, które będzie przekazywał metodę. Jeśli nie podasz nazwę parametru, Kreator ignoruje wszelkie atrybuty parametru (tylko ATL) lub **typ parametru** wybrane opcje.

  Po wybraniu **Dodaj**, nazwa parametru jest wyświetlana w **listy parametrów**.

  > [!NOTE]
  > Jeśli należy podać nazwę parametru, a następnie wybierz pozycję **Zakończ** przed wybraniem **Dodaj**, parametr nie jest dodawany do metody. Należy znaleźć metody i wstawić parametr ręcznie.

- **Add**

  Dodaje parametr należy określić w **Nazwa parametru**i jego atrybuty typu i parametr do **listy parametrów**. Wybierz **Dodaj** Aby dodać parametr do listy.

- **Usuń**

  Usuwa parametr w **listy parametrów** z listy.

- **Lista parametrów**

  Wyświetla wszystkie parametry i ich Modyfikatory i typów dodanych w aktualnie dla metody. W miarę dodawania parametrów, kreator dokona aktualizacji **listy parametrów** do wyświetlenia każdego parametru, z modyfikatora i typu.

## <a name="idl-attributes-add-method-wizard"></a>Atrybuty IDL, Kreator dodawania metody

Ta strona kreatora dodawania metody umożliwia Określ jakiekolwiek ustawienia interfejsu definicja języka (IDL) dla metody.

- `id`

  Ustawia identyfikator numeryczny, który identyfikuje metodę. Aby uzyskać więcej informacji, zobacz [identyfikator](/windows/desktop/Midl/id) w *odwołania MIDL*.

  To pole jest niedostępna dla interfejsów niestandardowych i nie jest dostępna dla MFC dispinterfaces.

- `call_as`

  Określa nazwę metody zdalnej, do którego ta metoda lokalne mogą być mapowane. Aby uzyskać więcej informacji, zobacz [call_as](/windows/desktop/Midl/call-as) w *odwołania MIDL*.

  Niedostępne dla MFC dispinterfaces.

- `helpcontext`

  Określa identyfikator kontekstu, który pozwala użytkownikowi oglądać informacje o tej metody w pliku pomocy. Aby uzyskać więcej informacji, zobacz [helpcontext —](/windows/desktop/Midl/helpcontext) w *odwołania MIDL*.

  Niedostępne dla MFC dispinterfaces.

- `helpstring`

  Określa ciąg znaków, który jest używany do opisania elementu, do której jest stosowany. Jest ona ustawiona domyślnie "Metoda *nazwę metody*." Aby uzyskać więcej informacji, zobacz [HelpString —](/windows/desktop/Midl/helpstring) w *odwołania MIDL*.

  Niedostępne dla MFC dispinterfaces.

- **Dodatkowe atrybuty**

  Niedostępne dla MFC dispinterfaces.

  |Atrybut|Opis|
  |---------------|-----------------|
  |`hidden`|Wskazuje, że metoda istnieje, ale nie powinien być wyświetlany w przeglądarce zorientowanej na użytkownika. Aby uzyskać więcej informacji, zobacz [ukryte](/windows/desktop/Midl/hidden) w *odwołania MIDL*.|
  |`source`|Wskazuje, że członek metoda jest źródłem zdarzeń. Aby uzyskać więcej informacji, zobacz [źródła](/windows/desktop/Midl/source) w *odwołania MIDL*.|
  |`local`|Określa kompilatorowi MIDL, że metoda nie jest zdalny. Aby uzyskać więcej informacji, zobacz [lokalnego](/windows/desktop/Midl/local) w *odwołania MIDL*.|
  |`restricted`|Określa, że metoda nie może być wywoływana arbitralnie. Aby uzyskać więcej informacji, zobacz [ograniczeniami](/windows/desktop/Midl/restricted) w *odwołania MIDL*.|
  |`vararg`|Określa, że ta metoda przyjmuje zmienną liczbę argumentów. Aby to osiągnąć, ostatni argument musi być bezpieczną tablicą o `VARIANT` typ, który zawiera pozostałymi argumentami. Aby uzyskać więcej informacji, zobacz [vararg](/windows/desktop/Midl/vararg) w *odwołania MIDL*.|
