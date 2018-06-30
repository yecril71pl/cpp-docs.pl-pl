---
title: 'TN006: Mapy wiadomości | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 06/25/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.messages.maps
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2c4bc820c6b54e055235c1bd29bd55ccfc032c92
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37121679"
---
# <a name="tn006-message-maps"></a>TN006: mapy komunikatów

Ta uwaga opisuje funkcja mapy komunikatów MFC.

## <a name="the-problem"></a>Problem

Microsoft Windows implementuje funkcje wirtualne w klasach okna, które skorzystać z jego funkcji obsługi komunikatów. Z powodu dużej liczby komunikatów związane zapewnienie osobnych funkcji wirtualnej dla każdej wiadomości Windows spowodowałoby vtable zbyt duża.

Ponieważ liczbę komunikatów zdefiniowanych w systemie Windows zmienia się wraz z upływem czasu, ponieważ aplikacje można zdefiniować własne komunikaty systemu Windows, mapy wiadomości zapewnienia poziomu pośredni uniemożliwiający istniejący kod fundamentalne zmiany interfejsu.

## <a name="overview"></a>Omówienie

MFC stanowi alternatywę dla instrukcji switch, który był używany w tradycyjnych programów systemu Windows do obsługi wiadomości wysyłane do okna. Mapowanie komunikatów do metod można zdefiniować tak, aby po odebraniu komunikatu przez okno odpowiednie metoda jest wywoływana automatycznie. Tej funkcji mapy komunikatów zaprojektowano tak, aby przypominały funkcje wirtualne, ale ma dodatkowe korzyści z funkcji wirtualnych C++ nie jest możliwe.

## <a name="defining-a-message-map"></a>Definiowanie mapy komunikatów

[Declare_message_map —](reference/message-map-macros-mfc.md#declare_message_map) Makro deklaruje trzy elementy członkowskie klasy.

- Wywołuje tablicy prywatnej wpisów AFX_MSGMAP_ENTRY *_messageEntries*.

- Wywołuje chronionych struktury AFX_MSGMAP *messageMap* wskazującego *_messageEntries* tablicy.

- A chronione funkcji wirtualnej o nazwie `GetMessageMap` zwracającą adres *messageMap*.

To makro należy umieścić w deklaracji klasy przy użyciu mapy komunikatów. Według Konwencji jest na końcu deklaracji klasy. Na przykład:

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

Jest to format wygenerowanych przez kreatorami AppWizard i ClassWizard podczas tworzenia nowych klas. / / {{I / /}} nawiasy kwadratowe są potrzebne dla ClassWizard.

Mapy wiadomości tabela będzie zdefiniowana przy użyciu zestawu makr, które rozszerzają na wpisy mapy wiadomości. Tabela rozpoczyna się od [begin_message_map —](reference/message-map-macros-mfc.md#begin_message_map) wywołanie makra, który definiuje klasę, która jest obsługiwany przez ten mapy komunikatów i klasy nadrzędnej, do którego są przekazywane nieobsługiwany wiadomości. Kończy tabeli [end_message_map —](reference/message-map-macros-mfc.md#end_message_map) wywołanie makra.

Między wywołaniami tych dwóch makro jest wpis dla każdego komunikatu mają być obsługiwane przez ten mapy komunikatów. Każdy standardowych komunikatów systemu Windows ma makra w postaci ON_WM_*MESSAGE_NAME* generujący wpis dla tej wiadomości.

Podpis standardowa funkcja został zdefiniowany dla rozpakowanie parametrach każdy komunikat systemu Windows i zapewnienia bezpieczeństwa typu. Te podpisy można znaleźć w pliku Afxwin.h w deklaracji z [CWnd](../mfc/reference/cwnd-class.md). Każdy z nich jest oznaczona jako ze słowem kluczowym **afx_msg** ułatwiający identyfikację.

> [!NOTE]
> ClassWizard wymaga użycia **afx_msg** — słowo kluczowe w Twojej deklaracje obsługi mapy wiadomości.

 Te podpisy funkcja uzyskano przy użyciu prostego Konwencji. Nazwa funkcji zawsze rozpoczyna się od `"On`". To jest następuje nazwa komunikatów systemu Windows z "WM_" usunięte i pierwszą literę każdego wyrazu kapitalizacji. Kolejność parametrów jest *wParam* następuje `LOWORD`(*lParam*) następnie `HIWORD`(*lParam*). Nieużywane parametry nie są przekazywane. Wszystkie dojścia, które są kodowane przez klasy MFC są konwertowane na wskaźniki do odpowiednich obiektów MFC. Poniższy przykład przedstawia sposób obsłużyć komunikat WM_PAINT i spowodować `CMyWnd::OnPaint` funkcja wywoływana:

```cpp
BEGIN_MESSAGE_MAP(CMyWnd, CMyParentWndClass)
    //{{AFX_MSG_MAP(CMyWnd)
    ON_WM_PAINT()
    //}}AFX_MSG_MAP
END_MESSAGE_MAP()
```

 Tabela mapy komunikatów musi być zdefiniowana poza zakresem żadnych definicji funkcji lub klasy. Nie należy go umieścić w bloku "C" extern.

> [!NOTE]
> ClassWizard zmodyfikuje wpisy mapy wiadomości, które mają miejsce między / / {{i / /}} komentarz nawiasu.

## <a name="user-defined-windows-messages"></a>Komunikaty systemu Windows zdefiniowane przez użytkownika

Wiadomości zdefiniowane przez użytkownika może być zawarta w mapie komunikatów przy użyciu [on_message —](reference/message-map-macros-mfc.md#on_message) makra. To makro akceptuje liczba wiadomości, a także metodę formularza:

```cpp
    // inside the class declaration
    afx_msg LRESULT OnMyMessage(WPARAM wParam, LPARAM lParam);

    #define WM_MYMESSAGE (WM_USER + 100)

BEGIN_MESSAGE_MAP(CMyWnd, CMyParentWndClass)
    ON_MESSAGE(WM_MYMESSAGE, OnMyMessage)
END_MESSAGE_MAP()
```

W tym przykładzie nawiązanie obsługi niestandardowego komunikatu, który ma identyfikator wiadomości Windows pochodzi od standardowego WM_USER podstawa wiadomości zdefiniowane przez użytkownika. Poniższy przykład przedstawia sposób wywołania tej obsługi:

```cpp
CWnd* pWnd = ...;
pWnd->SendMessage(WM_MYMESSAGE);
```

Zakres wiadomości zdefiniowane przez użytkownika, które posłuż się tą metodą musi być z zakresu WM_USER 0x7fff.

> [!NOTE]
> ClassWizard nie obsługuje wprowadzanie procedury obsługi on_message — ClassWizard interfejsu użytkownika. Należy ręcznie wprowadzić je w edytorze programu Visual C++. ClassWizard będzie analizować te wpisy i pozwalają na przeglądanie ich podobnie jak inne wpisy mapy wiadomości.

## <a name="registered-windows-messages"></a>Komunikaty systemu Windows w zarejestrowany

[RegisterWindowMessage](http://msdn.microsoft.com/library/windows/desktop/ms644947) funkcja służy do definiowania nowych komunikatów okien, który jest musi być unikatowy w całym systemie. On_registered_message — makro jest używane do obsługi tych wiadomości. To makro akceptuje nazwę *UINT NIEMAL* zmienna, która zawiera identyfikator komunikatu zarejestrowanych systemu windows. Na przykład

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

Musi być zarejestrowany zmienna Identyfikatora komunikatów systemu Windows (WM_FIND w tym przykładzie) *NEAR* zmiennej ze względu na sposób on_registered_message — jest zaimplementowana.

Zakres wiadomości zdefiniowane przez użytkownika, które posłuż się tą metodą będzie należeć do zakresu 0xC000 do 0xFFFF.

> [!NOTE]
> ClassWizard nie obsługuje wprowadzanie procedury obsługi on_registered_message — ClassWizard interfejsu użytkownika. Należy ręcznie wprowadzić je w edytorze tekstowym. ClassWizard będzie analizować te wpisy i pozwalają na przeglądanie ich podobnie jak inne wpisy mapy wiadomości.

## <a name="command-messages"></a>Komunikaty poleceń

Komunikaty poleceń z menu i akceleratorami są obsługiwane w mapy komunikatów z on_command — makro. To makro akceptuje identyfikator polecenia, a także metodę. Tylko WM_COMMAND komunikat zawierający *wParam* równa określone polecenie identyfikator jest obsługiwane przez metody określonej we wpisie mapy komunikatów. Funkcje Członkowskie programu obsługi poleceń nie mają żadnych parametrów i zwraca **void**. Makro ma następujący format:

```cpp
ON_COMMAND(id, memberFxn)
```

Polecenie aktualizacji wiadomości są kierowane przez ten sam mechanizm, ale zamiast tego użyj on_update_command_ui — makro. Funkcje Członkowskie programu obsługi aktualizacji poleceń przyjmować jeden parametr, wskaźnik do [CCmdUI](../mfc/reference/ccmdui-class.md) obiektu i zwraca **void**. Makro ma postać

```cpp
ON_UPDATE_COMMAND_UI(id, memberFxn)
```

Zaawansowani użytkownicy mogą używać on_command_ex — makro, czyli rozszerzonej formy polecenie Programy obsługi komunikatów. Makro stanowi nadzbiór funkcji on_command —. Funkcje Członkowskie program obsługi poleceń rozszerzonej przyjmować jeden parametr, **UINT** zawiera identyfikator polecenia i zwracać **BOOL**. Wartość zwracana powinna być **TRUE** aby wskazać, że polecenie zostało obsłużone. W przeciwnym razie routingu będzie innych obiektów docelowych polecenia.

Przykłady formach:

- Wewnątrz Resource.h (zwykle generowane przez Visual C++)

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

- W definicji mapy wiadomości

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

 Użytkownicy wersji Advanced może obsłużyć szeroką gamę poleceń za pomocą jednego polecenia program obsługi: [on_command_range —](reference/message-map-macros-mfc.md#on_command_range) lub on_command_range_ex —. Zobacz dokumentację produktu, aby uzyskać więcej informacji na temat makr.

> [!NOTE]
> ClassWizard obsługuje tworzenie on_command — i on_update_command_ui — programy obsługi, ale nie obsługuje tworzenia on_command_ex — lub on_command_range — programy obsługi. Jednak Kreator klas analizowanie i pozwalają na przeglądanie wszystkich wariantów obsługi cztery polecenia.

## <a name="control-notification-messages"></a>Komunikaty powiadomień dotyczących formantu

Wpis mapy komunikatów wysyłanych z formantów podrzędnych z oknem określono dodatkowy bitu informacji w swojej wiadomości: identyfikator formantu. Program obsługi komunikatów określony we wpisie mapy wiadomości jest wywoływana tylko wtedy, gdy są spełnione następujące warunki:

- Kod powiadamiania kontrolki (wyższe słowo *lParam*), takich jak BN_CLICKED, zgodny z kodem powiadomień, określony we wpisie mapy komunikatów.

- Identyfikator formantu (*wParam*) jest zgodny z Identyfikatorem formantu określony we wpisie mapy komunikatów.

Komunikaty powiadomień dotyczących Kontrolki niestandardowe mogą używać [on_control —](reference/message-map-macros-mfc.md#on_control) makro do definiowania wpisu mapy wiadomości, przy użyciu kodu niestandardowego powiadomień. To makro ma postać

```cpp
ON_CONTROL(wNotificationCode, id, memberFxn)
```

Zaawansowane wykorzystanie [on_control_range —](reference/message-map-macros-mfc.md#on_control_range) może służyć do obsługi określonego formantu powiadomienie z zakresu od formantów za pomocą tej procedury obsługi.

> [!NOTE]
> ClassWizard nie obsługuje tworzenia on_control — lub on_control_range — program obsługi w interfejsie użytkownika. Należy ręcznie wprowadzić je w edytorze tekstu. ClassWizard będzie analizować te wpisy i pozwalają na przeglądanie ich podobnie jak inne wpisy mapy wiadomości.

Formanty standardowe systemu Windows użyj bardziej zaawansowanych [WM_NOTIFY](http://msdn.microsoft.com/library/windows/desktop/bb775583) dla powiadomień dotyczących formantów złożonych. Ta wersja MFC ma bezpośrednią obsługę tej nowej wiadomości przy użyciu makra ON_NOTIFY i on_notify_range —. Zobacz dokumentację produktu, aby uzyskać więcej informacji na temat makr.

## <a name="see-also"></a>Zobacz także

[Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)  
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)  
