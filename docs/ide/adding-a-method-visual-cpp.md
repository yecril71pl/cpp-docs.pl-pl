---
title: Dodawanie metody
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
ms.openlocfilehash: b0c8ddabc4ed08fd217545bad269f0b2e48dd49e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69509539"
---
# <a name="add-a-method"></a>Dodawanie metody

Aby dodać metodę do interfejsu w projekcie, można użyć [Kreatora dodawania metody](#add-method-wizard) . Jeśli projekt zawiera klasę skojarzoną z interfejsem, Kreator modyfikuje także klasę.

**Aby dodać metodę do obiektu:**

1. W **Widok klasy**rozwiń węzeł projektu, aby wyświetlić interfejs, do którego chcesz dodać metodę.

   > [!NOTE]
   > Można również dodać metody do dispinterfaces, które, chyba że projekt jest przypisany do węzła biblioteki.

1. Kliknij prawym przyciskiem myszy nazwę interfejsu.

1. W menu skrótów wybierz polecenie **Dodaj**, a następnie wybierz polecenie **Dodaj metodę**.

1. W Kreatorze dodawania metody podaj informacje, aby utworzyć metodę.

1. Określ ustawienia języka definicji interfejsu dla tej metody na stronie [atrybuty IDL](#idl-attributes-add-method-wizard) kreatora.

1. Wybierz pozycję **Zakończ** , aby dodać metodę.

## <a name="in-this-section"></a>W tej sekcji

- [Kreator dodawania metody](#add-method-wizard)
- [Atrybuty IDL, Kreator dodawania metody](#idl-attributes-add-method-wizard)

## <a name="add-method-wizard"></a>Kreator dodawania metody

Użyj tego kreatora, aby dodać metodę do interfejsu. W zależności od typu projektu lub typu interfejsu, do którego dodawana jest metoda, Kreator wyświetla różne opcje.

### <a name="names"></a>Nazwy

- **Typ zwracany**

  Typ danych zwracanych przez metodę. `HRESULT`zalecane dla wszystkich typów interfejsów, ponieważ oferuje standardowy sposób zwracania błędów.

  |Typ interfejsu|Opis|
  |--------------------|-----------------|
  |Podwójny interfejs|`HRESULT`. Można zmienić.|
  |Niestandardowy interfejs|`HRESULT`. Można zmienić.|
  |Lokalny interfejs niestandardowy|Podaj własny typ zwracany lub wybierz z listy.|
  |Dispinterface|Podaj własny typ zwracany lub wybierz z listy.|
  |Kontrolka ActiveX MFC dispinterface|W przypadku zaimplementowania metody giełdowej dla zwracanego typu jest ustawiana odpowiednia wartość i nie można jej zmienić. W przypadku wybrania metody z listy **Nazwa metody** i wybrania opcji **niestandardowe** w obszarze **Wybierz typ metody**wybierz z listy typ zwracany.|

- **Nazwa metody**

  Ustawia nazwę metody.

  |Typ interfejsu|Opis|
  |--------------------|-----------------|
  |Interfejs ATL Dual Interface, niestandardowy interfejs i lokalny|Podaj własną nazwę metody.|
  |MFC dispinterface|Podaj własną nazwę metody lub wybierz sugerowaną nazwę metody z listy. Jeśli wybierzesz nazwę z listy, odpowiednia wartość zostanie wyświetlona w polu **Typ zwracany** i nie można jej zmienić.|
  |Kontrolka ActiveX MFC dispinterface|Podaj własne lub wybierz jedną z metod podstawowych [DoClick](../mfc/reference/colecontrol-class.md#doclick) i [Odśwież](../mfc/reference/colecontrol-class.md#refresh). Aby uzyskać więcej informacji, [Zobacz kontrolki ActiveX MFC: Dodawanie metod](../mfc/mfc-activex-controls-adding-stock-methods.md)podstawowych.|

- **Typ metody**

  Dostępne tylko dla kontrolek ActiveX MFC. W przypadku podania nazwy metody w polu **Nazwa metody** zamiast wybierania metody z listy to pole jest niedostępne.

  W przypadku wybrania jednej z metod z listy **Nazwa metody** wybierz implementację giełdową lub implementację niestandardową.

  |Typ metody|Opis|
  |-----------------|-----------------|
  |**Stanu**|Domyślnie. Wstawia implementację giełdową metody wybranej na liście **Nazwa metody** . Nie można zmienić **zwracanego typu** , jeśli wybierzesz opcję **Zapasy**.|
  |**Custom**|Wstawia implementację klasy zastępczej metody wybranej na liście **Nazwa metody** . W przypadku typów metod niestandardowych można podać własny typ zwracany lub wybrać jeden z listy **Typ zwracany** .|

- **Nazwa wewnętrzna**

  Dostępne tylko dla metod niestandardowych dodanych do dispinterface MFC. Ustawia nazwę używaną na mapie wysyłania, plik nagłówka (. h) i plik implementacji (. cpp). Domyślnie ta nazwa jest taka sama jak **Nazwa metody**. Możesz zmienić nazwę metody, jeśli pracujesz z dispinterface MFC lub dodajesz metodę niestandardową do kontrolki ActiveX MFC dispinterface.

  |Typ interfejsu|Opis|
  |--------------------|-----------------|
  |Interfejs ATL Dual Interface, niestandardowy interfejs i lokalny|Niedostępne.|
  |MFC dispinterface|Domyślnie Ustaw nazwę metody. Można edytować nazwę wewnętrzną.|
  |Kontrolka ActiveX MFC dispinterface|Nazwę wewnętrzną można ustawić tylko dla metod niestandardowych. Metody podstawowe nie używają nazwy wewnętrznej.|

- **Atrybuty parametru**

  Ustawia wszelkie dodatkowe atrybuty parametru określonego w polu **Nazwa parametru**.

  |Atrybut parametru|Opis|Dozwolone kombinacje|
  |-------------------------|-----------------|--------------------------|
  |**W**|Wskazuje, że parametr jest przesyłany z procedury wywołującej do procedury wywoływanej.|`in`jedyn<br /><br /> `in` i `out`|
  |**Określoną**|Wskazuje, że parametr wskaźnika jest zwracany z wywoływanej procedury do procedury wywołującej (z serwera do klienta).|`out`jedyn<br /><br /> `in` i `out`<br /><br /> `out` i `retval`|
  |**Retval**|Wskazuje, że parametr otrzymuje wartość zwracaną przez element członkowski.|`retval` i `out`|

- **Typ parametru**

  Ustawia typ danych parametru. Wybierz typ z listy.

- **Nazwa parametru**

  Ustawia nazwę parametru, który ma zostać przekazany przez metodę. Po wpisaniu nazwy wybierz pozycję **Dodaj** , aby dodać ją do listy parametrów, które będą przekazywane przez metodę. Jeśli nie podano nazwy parametru, Kreator zignoruje wszystkie atrybuty parametrów (tylko ATL) lub **Typ parametru** .

  Po wybraniu opcji **Dodaj**Nazwa parametru zostanie wyświetlona na **liście parametrów**.

  > [!NOTE]
  > Jeśli podasz nazwę parametru, a następnie wybierzesz pozycję **Zakończ** przed wybraniem opcji **Dodaj**, parametr nie zostanie dodany do metody. Należy znaleźć metodę i wstawić parametr ręcznie.

- **Add**

  Dodaje parametr określony w polu **Nazwa parametru**oraz jego atrybuty typu i parametru do **listy parametrów**. Wybierz pozycję **Dodaj** , aby dodać parametr do listy.

- **Usuń**

  Usuwa parametr wybrany na **liście parametrów** z listy.

- **Lista parametrów**

  Wyświetla wszystkie parametry i ich modyfikatory i typy aktualnie dodane dla metody. Podczas dodawania parametrów Kreator aktualizuje **listę parametrów** , aby wyświetlić każdy parametr z jego modyfikatorem i typem.

## <a name="idl-attributes-add-method-wizard"></a>Atrybuty IDL, Kreator dodawania metody

Użyj tej strony Kreatora dodawania metody, aby określić ustawienia języka definicji interfejsu (IDL) dla tej metody.

- `id`

  Ustawia identyfikator liczbowy identyfikujący metodę. Aby uzyskać więcej informacji, zobacz [ID](/windows/win32/Midl/id) w *MIDL Reference*.

  To pole jest niedostępne dla interfejsów niestandardowych i nie jest dostępne dla MFC dispinterfaces.

- `call_as`

  Określa nazwę metody zdalnej, do której można zamapować tę metodę lokalną. Aby uzyskać więcej informacji, zobacz [call_as](/windows/win32/Midl/call-as) in the *MIDL Reference*.

  Niedostępne dla MFC dispinterfaces.

- `helpcontext`

  Określa identyfikator kontekstu, który umożliwia użytkownikowi wyświetlanie informacji o tej metodzie w pliku pomocy. Aby uzyskać więcej informacji, zobacz [atrybut HelpContext](/windows/win32/Midl/helpcontext) in the *MIDL Reference*.

  Niedostępne dla MFC dispinterfaces.

- `helpstring`

  Określa ciąg znaków, który jest używany do opisania elementu, do którego ma zastosowanie. Jest ona domyślnie ustawiona na wartość " *Nazwa metody*metody". Aby uzyskać więcej informacji, zobacz [HelpString](/windows/win32/Midl/helpstring) in the *MIDL Reference*.

  Niedostępne dla MFC dispinterfaces.

- **Dodatkowe atrybuty**

  Niedostępne dla MFC dispinterfaces.

  |Atrybut|Opis|
  |---------------|-----------------|
  |`hidden`|Wskazuje, że metoda istnieje, ale nie powinna być wyświetlana w przeglądarce zorientowanej na użytkownika. Aby uzyskać więcej informacji, zobacz [Hidden](/windows/win32/Midl/hidden) in *MIDL Reference*.|
  |`source`|Wskazuje, że element członkowski metody jest źródłem zdarzeń. Aby uzyskać więcej informacji, zobacz [Źródło](/windows/win32/Midl/source) w *MIDL Reference*.|
  |`local`|Określa kompilatorowi MIDL, że metoda nie jest zdalna. Aby uzyskać więcej informacji, zobacz [Local](/windows/win32/Midl/local) in the *MIDL Reference*.|
  |`restricted`|Określa, że metoda nie może być wywoływana arbitralnie. Aby uzyskać więcej informacji, [](/windows/win32/Midl/restricted) Zobacz artykuł z ograniczeniami w *MIDL Reference*.|
  |`vararg`|Określa, że metoda przyjmuje zmienną liczbę argumentów. Aby to osiągnąć, ostatni argument musi być bezpieczną tablicą `VARIANT` typu, która zawiera resztę argumentów. Aby uzyskać więcej informacji, zobacz [vararg](/windows/win32/Midl/vararg) w *MIDL Reference*.|
