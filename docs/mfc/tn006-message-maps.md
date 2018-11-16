---
title: 'TN006: mapy komunikatów'
ms.date: 06/25/2018
f1_keywords:
- vc.messages.maps
helpviewer_keywords:
- ON_UPDATE_COMMAND_UI macro [MFC]
- ON_NOTIFY_RANGE macro [MFC]
- ON_COMMAND macro [MFC]
- ON_CONTROL_RANGE macro [MFC]
- ON_REGISTERED_MESSAGE macro [MFC]
- ON_NOTIFY message [MFC]
- ON_COMMAND_RANGE_EX macro [MFC]
- ON_MESSAGE macro [MFC]
- Windows messages [MFC], message maps
- ON_COMMAND_RANGE macro [MFC]
- TN006
- ON_CONTROL macro [MFC]
- ON_COMMAND_EX macro [MFC]
- message maps [MFC], Windows messaging
ms.assetid: af4b6794-4b40-4f1e-ad41-603c3b7409bb
ms.openlocfilehash: ab08476923f253d666e024d8944aec64ed0af8da
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/15/2018
ms.locfileid: "51693678"
---
# <a name="tn006-message-maps"></a>TN006: mapy komunikatów

Ta uwaga opisuje funkcja mapy komunikatów MFC.

## <a name="the-problem"></a>Ten Problem

Program Microsoft Windows implementuje funkcje wirtualne w klasach okien, korzystających z jego możliwości obsługi komunikatów. Z powodu dużej liczby komunikatów związane dostarczanie oddzielne funkcję wirtualną dla każdego komunikatu Windows utworzyć niezwykle dużych vtable.

Ponieważ liczba komunikatów zdefiniowaną przez system Windows zmienia się wraz z upływem czasu, ponieważ aplikacje można zdefiniować własne komunikatów Windows, mapy wiadomości zapewniają poziom pośrednictwa, który uniemożliwia zmian w istniejącym kodzie zmiany w interfejsie.

## <a name="overview"></a>Omówienie

MFC stanowi alternatywę dla instrukcji switch, który był używany w tradycyjnych programów Windows do obsługi wiadomości wysyłane do okna. Mapowanie komunikatów do metod można zdefiniować tak, aby po otrzymaniu komunikatu przez okno odpowiedniej metody jest wywoływana automatycznie. Tej funkcji w mapie komunikatów zaprojektowano tak, aby przypominały funkcje wirtualne, ale ma dodatkowych korzyści, nie jest możliwe dzięki funkcji wirtualnych języka C++.

## <a name="defining-a-message-map"></a>Definiowanie mapy komunikatów

[DECLARE_MESSAGE_MAP](reference/message-map-macros-mfc.md#declare_message_map) Makro deklaruje trzy elementy członkowskie klasy.

- Wywołuje prywatne tablicę wpisy AFX_MSGMAP_ENTRY *_messageEntries*.

- Wywołuje chroniony struktury AFX_MSGMAP *messageMap* wskazującej *_messageEntries* tablicy.

- Chroniona funkcja wirtualna wywoływana w `GetMessageMap` zwracającego adres *messageMap*.

To makro, należy umieścić w deklaracji klasy za pomocą mapy komunikatów. Według Konwencji jest na końcu deklaracji klasy. Na przykład:

```cpp
class CMyWnd : public CMyParentWndClass
{
    // my stuff...

protected:
    //{{AFX_MSG(CMyWnd)
    afx_msg void OnPaint();
    //}}AFX_MSG

    DECLARE_MESSAGE_MAP()
};
```

Ten format jest używany generowane przez kreatora AppWizard i ClassWizard podczas tworzenia nowych klas. / / {{I / /}} nawiasy są wymagane przez ClassWizard.

Tabela mapy wiadomości jest zdefiniowana za pomocą zestawu makr, które na wpisy mapy komunikatów. Tabela zaczyna się od [BEGIN_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_message_map) wywołanie makra, który definiuje klasę, która jest obsługiwana przez tę mapę komunikatów i klasy nadrzędnej, do której są przekazywane nieobsługiwany wiadomości. Tabela kończy się [END_MESSAGE_MAP](reference/message-map-macros-mfc.md#end_message_map) wywołania makra.

Między wywołaniami następujące dwa makra jest wpis dla każdego komunikatu, które mają być obsługiwane przez tę mapę komunikatów. Każda standardowa wiadomość Windows ma makra w postaci ON_WM_*MESSAGE_NAME* generujący wpis dla tego komunikatu.

Podpis funkcji standardowej został zdefiniowany dla rozpakowywania parametrów każdego komunikatu Windows i zapewnienia bezpieczeństwa typu. Te podpisy można znaleźć w pliku Afxwin.h w deklaracji elementu [CWnd](../mfc/reference/cwnd-class.md). Każdy z nich jest oznaczona za pomocą słowa kluczowego **afx_msg** ułatwiający identyfikację.

> [!NOTE]
> ClassWizard wymaga użycia **afx_msg** — słowo kluczowe w swojej deklaracji obsługi mapy wiadomości.

Te sygnatur funkcji uzyskano przy użyciu prostego Konwencji. Nazwa funkcji zawsze zaczyna się od `"On`". To następuje nazwa komunikatu Windows za pomocą "WM_" usunięte i pierwszą literę każdego wyrazu wielką literą. Kolejność parametrów jest *wParam* następuje `LOWORD`(*lParam*) następnie `HIWORD`(*lParam*). Nieużywane parametry nie są przekazywane. Wszystkie dojścia, które zostaną opakowane przy klas MFC są konwertowane do wskaźników do odpowiednich obiektów MFC. Poniższy przykład pokazuje, jak obsłużyć komunikat WM_PAINT i spowodować, że `CMyWnd::OnPaint` funkcja do wywołania:

```cpp
BEGIN_MESSAGE_MAP(CMyWnd, CMyParentWndClass)
    //{{AFX_MSG_MAP(CMyWnd)
    ON_WM_PAINT()
    //}}AFX_MSG_MAP
END_MESSAGE_MAP()
```

Tabela mapy wiadomości muszą być zdefiniowane poza zakresem dowolna definicja funkcji lub klasy. Nie należy go umieścić w bloku extern "C".

> [!NOTE]
> ClassWizard modyfikuje wpisy mapy komunikatów, które mają miejsce między / / {{i / /}} komentarz w nawiasie kwadratowym.

## <a name="user-defined-windows-messages"></a>Komunikaty Windows zdefiniowane przez użytkownika

Wiadomości zdefiniowanych przez użytkownika może być zawarta w mapie komunikatów za pomocą [ON_MESSAGE](reference/message-map-macros-mfc.md#on_message) makra. To makro akceptuje numer komunikatu i metody formularza:

```cpp
    // inside the class declaration
    afx_msg LRESULT OnMyMessage(WPARAM wParam, LPARAM lParam);

    #define WM_MYMESSAGE (WM_USER + 100)

BEGIN_MESSAGE_MAP(CMyWnd, CMyParentWndClass)
    ON_MESSAGE(WM_MYMESSAGE, OnMyMessage)
END_MESSAGE_MAP()
```

W tym przykładzie możemy nawiązać Obsługa wiadomość niestandardowa, która ma identyfikator komunikatu Windows pochodną WM_USER Standardowa podstawa wiadomości zdefiniowanych przez użytkownika. Poniższy przykład pokazuje sposób wywołania tej procedury obsługi:

```cpp
CWnd* pWnd = ...;
pWnd->SendMessage(WM_MYMESSAGE);
```

Zakres komunikatów zdefiniowanych przez użytkownika, korzystających z tej metody musi być z zakresu WM_USER 0x7fff.

> [!NOTE]
> ClassWizard nie obsługuje wprowadzanie procedury obsługi ON_MESSAGE z ClassWizard interfejsu użytkownika. Należy ręcznie wprowadzić je w Edytorze Visual C++. ClassWizard będzie analizować te wpisy i pozwalają na przeglądanie ich tak samo jak wszystkie inne wpisy mapy komunikatów.

## <a name="registered-windows-messages"></a>Windows zarejestrowanych komunikatów

[RegisterWindowMessage](https://msdn.microsoft.com/library/windows/desktop/ms644947) funkcja służy do definiowania nowego komunikatu w oknie, która może być unikatowy w całym systemie. Makro ON_REGISTERED_MESSAGE jest używane do obsługi komunikatów. To makro akceptuje nazwę *UINT NIEMAL* zmiennej, która zawiera identyfikator komunikatu zarejestrowanych systemu windows. Na przykład

```cpp
class CMyWnd : public CMyParentWndClass
{
public:
    CMyWnd();

    //{{AFX_MSG(CMyWnd)
    afx_msg LRESULT OnFind(WPARAM wParam, LPARAM lParam);
    //}}AFX_MSG

    DECLARE_MESSAGE_MAP()
};

static UINT NEAR WM_FIND = RegisterWindowMessage("COMMDLG_FIND");

BEGIN_MESSAGE_MAP(CMyWnd, CMyParentWndClass)
    //{{AFX_MSG_MAP(CMyWnd)
    ON_REGISTERED_MESSAGE(WM_FIND, OnFind)
    //}}AFX_MSG_MAP
END_MESSAGE_MAP()
```

Musi być zarejestrowany Windows zmienna Identyfikatora komunikatu (WM_FIND w tym przykładzie) *NEAR* ON_REGISTERED_MESSAGE zmiennej ze względu na sposób jest implementowany.

Zakres komunikatów zdefiniowanych przez użytkownika, korzystających z tego podejścia będzie należeć do zakresu 0xC000 do 0xFFFF.

> [!NOTE]
> ClassWizard nie obsługuje wprowadzanie procedury obsługi ON_REGISTERED_MESSAGE z ClassWizard interfejsu użytkownika. Należy ręcznie wprowadzić je w edytorze tekstowym. ClassWizard będzie analizować te wpisy i pozwalają na przeglądanie ich tak samo jak wszystkie inne wpisy mapy komunikatów.

## <a name="command-messages"></a>Komunikaty poleceń

Komunikaty poleceń z menu i akceleratorami są obsługiwane w mapy komunikatów za pomocą ON_COMMAND — makro. To makro akceptuje identyfikator polecenia i metody. Tylko określone wiadomości WM_COMMAND, który ma *wParam* równa określone polecenie identyfikator odbywa się w sposób określony w ramach wpisu mapy komunikatów. Funkcje Członkowskie programu obsługi poleceń nie mają żadnych parametrów i zwracają **void**. Makro ma następującą postać:

```cpp
ON_COMMAND(id, memberFxn)
```

Polecenie update wiadomości są przesyłane za pośrednictwem ten sam mechanizm, ale zamiast tego użyj ON_UPDATE_COMMAND_UI — makro. Funkcje Członkowskie programu obsługi aktualizacji poleceń przyjmować jeden parametr, wskaźnik do [CCmdUI](../mfc/reference/ccmdui-class.md) obiektu i zwraca **void**. Makro ma postać

```cpp
ON_UPDATE_COMMAND_UI(id, memberFxn)
```

Zaawansowani użytkownicy mogą używać ON_COMMAND_EX — makro, czyli rozszerzonej postaci polecenia programy obsługi komunikatów. Makro stanowi nadzbiór funkcji ON_COMMAND. Rozszerzona procedura obsługi polecenia elementów członkowskich przyjmować jeden parametr, **UINT** zawiera identyfikator polecenia i powrócić **BOOL**. Zwracana wartość powinna być **TRUE** do wskazania, że polecenie zostało obsłużone. W przeciwnym razie routingu będzie innych obiektów docelowych polecenia.

Przykłady z poniższych metod:

- Wewnątrz Resource.h (zwykle jest generowane przez Visual C++)

    ```cpp
    #define    ID_MYCMD      100
    #define    ID_COMPLEX    101
    ```

- Wewnątrz deklaracji klasy

    ```cpp
    afx_msg void OnMyCommand();
    afx_msg void OnUpdateMyCommand(CCmdUI* pCmdUI);
    afx_msg BOOL OnComplexCommand(UINT nID);
    ```

- W definicji mapy komunikatów

    ```cpp
    ON_COMMAND(ID_MYCMD, OnMyCommand)
    ON_UPDATE_COMMAND_UI(ID_MYCMD, OnUpdateMyCommand)
    ON_COMMAND_EX(ID_MYCMD, OnComplexCommand)
    ```

- W pliku implementacji

    ```cpp
    void CMyClass::OnMyCommand()
    {
        // handle the command
    }

    void CMyClass::OnUpdateMyCommand(CCmdUI* pCmdUI)
    {
        // set the UI state with pCmdUI
    }

    BOOL CMyClass::OnComplexCommand(UINT nID)
    {
        // handle the command
        return TRUE;
    }
    ```

Zaawansowani użytkownicy mogą obsługiwać szeroką gamę poleceń za pomocą jednego polecenia program obsługi: [ON_COMMAND_RANGE](reference/message-map-macros-mfc.md#on_command_range) lub ON_COMMAND_RANGE_EX. Zobacz dokumentację produktu, aby uzyskać więcej informacji na temat tych makr.

> [!NOTE]
> ClassWizard obsługuje tworzenie obsługi ON_COMMAND i ON_UPDATE_COMMAND_UI, ale nie obsługuje tworzenia ON_COMMAND_EX lub ON_COMMAND_RANGE programów obsługi. Jednak Kreator klas przeanalizować i pozwalają na przeglądanie wszystkich wariantów obsługi cztery polecenia.

## <a name="control-notification-messages"></a>Komunikaty powiadomień dotyczących kontrolki

Wiadomości, które są wysyłane z formantów podrzędnych do okna ma dodatkowy trochę informacji w ich wiadomości mapy wejścia: Identyfikator kontrolki. Program obsługi komunikatów, określone w wpis mapy wiadomości jest wywoływana tylko wtedy, gdy są spełnione następujące warunki:

- Kod powiadamiania kontrolki (wyższe słowo *lParam*), takie jak BN_CLICKED, dopasowuje kod powiadomienia określony we wpisie mapy komunikatów.

- Identyfikator formantu (*wParam*) zgodny z Identyfikatorem formantu określony we wpisie w mapie komunikatów.

Komunikaty powiadomień dotyczących Kontrolki niestandardowe mogą używać [ON_CONTROL](reference/message-map-macros-mfc.md#on_control) makra, aby zdefiniować wpis mapy wiadomości z kodem niestandardowe powiadomienie. To makro ma postać

```cpp
ON_CONTROL(wNotificationCode, id, memberFxn)
```

Zaawansowane wykorzystanie [ON_CONTROL_RANGE](reference/message-map-macros-mfc.md#on_control_range) może służyć do obsługi powiadomień sterowania z szeroką gamę elementów sterujących, za pomocą tej procedury obsługi.

> [!NOTE]
> ClassWizard nie obsługuje tworzenia nieprawidłowego ON_CONTROL lub ON_CONTROL_RANGE w interfejsie użytkownika. Należy ręcznie wprowadzić je za pomocą edytora tekstów. ClassWizard będzie analizować te wpisy i pozwalają na przeglądanie ich tak samo jak inne wpisy mapy komunikatów.

Wspólnych formantów Windows użyj bardziej wydajne [WM_NOTIFY](/windows/desktop/controls/wm-notify) dla powiadomień dotyczących formantów złożonych. Ta wersja programu MFC ma bezpośrednią obsługę tę nową wiadomość przy użyciu makr komunikaty ON_NOTIFY i ON_NOTIFY_RANGE. Zobacz dokumentację produktu, aby uzyskać więcej informacji na temat tych makr.

## <a name="see-also"></a>Zobacz także

[Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)<br/>
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)
