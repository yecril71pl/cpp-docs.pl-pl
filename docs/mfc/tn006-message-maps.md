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
ms.openlocfilehash: 6b387b851f5a76cd0d11957a87e57307d624759e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228534"
---
# <a name="tn006-message-maps"></a>TN006: mapy komunikatów

Ta Uwaga opisuje obiekt mapy komunikatów MFC.

## <a name="the-problem"></a>Problem

System Microsoft Windows implementuje funkcje wirtualne w klasach okien, które korzystają z funkcji obsługi komunikatów. Ze względu na dużą liczbę komunikatów, dostarczając osobną funkcję wirtualną dla każdego komunikatu systemu Windows, można utworzyć niezwykleą dużą tablicę.

Ze względu na to, że liczba zdefiniowanych przez system komunikatów systemu Windows zmienia się wraz z upływem czasu, a aplikacje mogą definiować własne komunikaty systemu Windows, mapy komunikatów udostępniają poziom pośredni, który uniemożliwia zmianę interfejsu z powodu nieprzerwanego istniejącego kodu.

## <a name="overview"></a>Omówienie

MFC stanowi alternatywę dla instrukcji switch, która została użyta w tradycyjnych programach opartych na systemie Windows do obsługi komunikatów wysyłanych do okna. Można zdefiniować mapowanie komunikatów do metod, aby po odebraniu komunikatu przez okno odpowiednia metoda jest wywoływana automatycznie. Ta funkcja mapy komunikatów jest zaprojektowana tak, aby wyglądała podobnie do funkcji wirtualnych, ale ma dodatkowe korzyści, które nie są możliwe w przypadku funkcji wirtualnych języka C++.

## <a name="defining-a-message-map"></a>Definiowanie mapy komunikatów

Makro [DECLARE_MESSAGE_MAP](reference/message-map-macros-mfc.md#declare_message_map) deklaruje trzy elementy członkowskie dla klasy.

- Prywatna tablica wpisów AFX_MSGMAP_ENTRY o nazwie *_messageEntries*.

- Struktura AFX_MSGMAP chronionej o nazwie *messageMap* , która wskazuje na tablicę *_messageEntries* .

- Chroniona funkcja wirtualna o nazwie `GetMessageMap` zwraca adres *messageMap*.

To makro należy umieścić w deklaracji dowolnej klasy przy użyciu map komunikatów. Zgodnie z Konwencją, znajduje się na końcu deklaracji klasy. Na przykład:

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

Jest to format generowany przez AppWizard i ClassWizard podczas tworzenia nowych klas. Nawiasy//{{i//}} są zbędne dla ClassWizard.

Tabela mapy komunikatów jest definiowana przy użyciu zestawu makr, które rozwijają się do wpisów mapy komunikatów. Tabela rozpoczyna się od wywołania makra [BEGIN_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_message_map) , które definiuje klasę, która jest obsługiwana przez tę mapę komunikatów i klasę nadrzędną, do której są przesyłane nieobsługiwane komunikaty. Tabela zostanie zakończona z wywołaniem makra [END_MESSAGE_MAP](reference/message-map-macros-mfc.md#end_message_map) .

Między tymi dwoma wywołaniami makr jest wpis dla każdego komunikatu, który ma być obsługiwany przez tę mapę komunikatów. Każdy standardowy komunikat systemu Windows zawiera makro ON_WM_*MESSAGE_NAME* , które generuje wpis dla tego komunikatu.

Zdefiniowano sygnaturę funkcji standardowej do rozpakowywania parametrów poszczególnych komunikatów systemu Windows i zapewnienia bezpieczeństwa typów. Podpisy te można znaleźć w pliku afxwin. h w deklaracji [CWnd](../mfc/reference/cwnd-class.md). Każda z nich jest oznaczona za pomocą słowa kluczowego **afx_msg** w celu ułatwienia identyfikacji.

> [!NOTE]
> ClassWizard wymaga użycia słowa kluczowego **afx_msg** w deklaracjach obsługi mapy komunikatów.

Te sygnatury funkcji były wyprowadzane przy użyciu prostej Konwencji. Nazwa funkcji zawsze zaczyna się od `"On` ". Następuje nazwa komunikatu systemu Windows z usuniętym identyfikatorem "WM_" i pierwszą literą każdego wyrazu. Kolejność parametrów to *wParam* , a `LOWORD` następnie (*lParam*), a następnie `HIWORD` (*lParam*). Nieużywane parametry nie są przesyłane. Wszystkie uchwyty, które są opakowane przez klasy MFC, są konwertowane na wskaźniki do odpowiednich obiektów MFC. Poniższy przykład pokazuje, jak obsłużyć komunikat WM_PAINT i spowodować `CMyWnd::OnPaint` wywołanie funkcji:

```cpp
BEGIN_MESSAGE_MAP(CMyWnd, CMyParentWndClass)
    //{{AFX_MSG_MAP(CMyWnd)
    ON_WM_PAINT()
    //}}AFX_MSG_MAP
END_MESSAGE_MAP()
```

Tabela mapy komunikatów musi być zdefiniowana poza zakresem dowolnej definicji funkcji lub klasy. Nie powinna być umieszczana w zewnętrznym bloku "C".

> [!NOTE]
> ClassWizard zmodyfikuje wpisy mapy komunikatów, które występują między nawiasem komentarza//{{i//}}.

## <a name="user-defined-windows-messages"></a>Komunikaty systemu Windows zdefiniowane przez użytkownika

Komunikaty zdefiniowane przez użytkownika mogą być dołączane do mapy komunikatów przy użyciu makra [ON_MESSAGE](reference/message-map-macros-mfc.md#on_message) . To makro akceptuje numer komunikatu i metodę formularza:

```cpp
    // inside the class declaration
    afx_msg LRESULT OnMyMessage(WPARAM wParam, LPARAM lParam);

    #define WM_MYMESSAGE (WM_USER + 100)

BEGIN_MESSAGE_MAP(CMyWnd, CMyParentWndClass)
    ON_MESSAGE(WM_MYMESSAGE, OnMyMessage)
END_MESSAGE_MAP()
```

W tym przykładzie ustanawiamy procedurę obsługi dla komunikatu niestandardowego, który ma identyfikator komunikatu systemu Windows pochodzący od standardowej bazy WM_USERej dla wiadomości zdefiniowanych przez użytkownika. Poniższy przykład pokazuje, jak wywołać tę procedurę obsługi:

```cpp
CWnd* pWnd = ...;
pWnd->SendMessage(WM_MYMESSAGE);
```

Zakres komunikatów zdefiniowanych przez użytkownika, które korzystają z tej metody, musi należeć do zakresu WM_USER do 0x7FFF.

> [!NOTE]
> ClassWizard nie obsługuje wprowadzania procedur obsługi ON_MESSAGE z interfejsu użytkownika ClassWizard. Należy wprowadzić je ręcznie w edytorze Visual C++. ClassWizard przeanalizuje te wpisy i umożliwi przeszukanie ich w taki sam sposób jak w przypadku innych wpisów mapy komunikatów.

## <a name="registered-windows-messages"></a>Zarejestrowane komunikaty systemu Windows

Funkcja [RegisterWindowMessage](/windows/win32/api/winuser/nf-winuser-registerwindowmessagew) służy do definiowania nowego komunikatu okna, który ma być unikatowy w całym systemie. ON_REGISTERED_MESSAGE makro służy do obsługi tych komunikatów. To makro akceptuje nazwę klasy uint w *sąsiedztwie* , która zawiera zarejestrowany Identyfikator komunikatu systemu Windows. Na przykład

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

Zarejestrowana zmienna identyfikatora komunikatu systemu Windows (WM_FIND w tym przykładzie) musi być *bliską* zmienną ze względu na sposób, w jaki ON_REGISTERED_MESSAGE jest zaimplementowany.

Zakres komunikatów zdefiniowanych przez użytkownika, które korzystają z tego podejścia, będzie w zakresie 0xC000 do 0xFFFF.

> [!NOTE]
> ClassWizard nie obsługuje wprowadzania procedur obsługi ON_REGISTERED_MESSAGE z interfejsu użytkownika ClassWizard. Należy wprowadzić je ręcznie z edytora tekstu. ClassWizard przeanalizuje te wpisy i umożliwi przeszukanie ich w taki sam sposób jak w przypadku innych wpisów mapy komunikatów.

## <a name="command-messages"></a>Komunikaty poleceń

Komunikaty poleceń z menu i akceleratorów są obsługiwane w mapach komunikatów za pomocą makra ON_COMMAND. To makro akceptuje identyfikator polecenia i metodę. Tylko określony WM_COMMAND komunikat, który ma *wParam* równy OKREŚLONEmu identyfikatorowi polecenia, jest obsługiwany przez metodę określoną we wpisie mapy komunikatów. Funkcje członkowskie procedury obsługi poleceń nie przyjmują parametrów i zwracają **`void`** . Makro ma następującą postać:

```cpp
ON_COMMAND(id, memberFxn)
```

Komunikaty aktualizacji poleceń są kierowane za pomocą tego samego mechanizmu, ale zamiast tego należy użyć makra ON_UPDATE_COMMAND_UI. Funkcja elementu członkowskiego obsługi aktualizacji polecenia przyjmuje jeden parametr, wskaźnik do obiektu [CCmdUI](../mfc/reference/ccmdui-class.md) i zwraca **`void`** . Makro ma postać

```cpp
ON_UPDATE_COMMAND_UI(id, memberFxn)
```

Użytkownicy zaawansowani mogą używać makra ON_COMMAND_EX, który jest rozszerzoną formą obsługi komunikatów poleceń. Makro zapewnia nadzbiór funkcji ON_COMMAND. Rozszerzone funkcje składowe programu obsługi poleceń przyjmują jeden parametr, **uint** , który zawiera identyfikator polecenia i zwracają wartość **logiczną**. Wartość zwracana powinna mieć wartość **true** , aby wskazać, że polecenie zostało obsłużone. W przeciwnym razie Routing będzie kontynuował inne obiekty docelowe poleceń.

Przykłady tych formularzy:

- Wewnątrz zasobu. h (zazwyczaj generowane przez Visual C++)

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

- Wewnątrz definicji mapy wiadomości

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

Użytkownicy zaawansowani mogą obsługiwać szereg poleceń za pomocą jednego programu obsługi poleceń: [ON_COMMAND_RANGE](reference/message-map-macros-mfc.md#on_command_range) lub ON_COMMAND_RANGE_EX. Zapoznaj się z dokumentacją produktu, aby uzyskać więcej informacji na temat tych makr.

> [!NOTE]
> ClassWizard obsługuje tworzenie programów obsługi ON_COMMAND i ON_UPDATE_COMMAND_UI, ale nie obsługuje tworzenia ON_COMMAND_EX lub ON_COMMAND_RANGE obsługi. Jednak Kreator klas przeanalizuje i umożliwi przeglądanie wszystkich czterech wariantów obsługi poleceń.

## <a name="control-notification-messages"></a>Sterowanie komunikatami powiadomień

Komunikaty wysyłane z formantów podrzędnych do okna zawierają dodatkowe informacje w ich wpisie mapy komunikatów: Identyfikator formantu. Procedura obsługi komunikatów określona w wpisie mapy komunikatów jest wywoływana tylko wtedy, gdy spełnione są następujące warunki:

- Kod powiadomienia sterującego (High Word of *lParam*), taki jak BN_CLICKED, pasuje do kodu powiadomienia określonego we wpisie mapy komunikatów.

- Identyfikator kontrolki (*wParam*) jest zgodny z identyfikatorem kontrolki określonym we wpisie mapy komunikatów.

Komunikaty powiadomień o kontrolkach niestandardowych mogą używać makra [ON_CONTROL](reference/message-map-macros-mfc.md#on_control) , aby zdefiniować wpis mapy komunikatów z niestandardowym kodem powiadomienia. To makro ma postać

```cpp
ON_CONTROL(wNotificationCode, id, memberFxn)
```

[ON_CONTROL_RANGE](reference/message-map-macros-mfc.md#on_control_range) zaawansowanego użycia może służyć do obsługi określonego powiadomienia kontroli z zakresu kontrolek z tą samą obsługą.

> [!NOTE]
> Usługa ClassWizard nie obsługuje tworzenia ON_CONTROL lub ON_CONTROL_RANGE obsługi w interfejsie użytkownika. Należy wprowadzić je ręcznie przy użyciu edytora tekstu. ClassWizard przeanalizuje te wpisy i umożliwi ich przeglądanie w taki sam sposób jak w przypadku innych wpisów mapy komunikatów.

Typowe formanty systemu Windows wykorzystują bardziej zaawansowane [WM_NOTIFY](/windows/win32/controls/wm-notify) w przypadku złożonych powiadomień o kontrolkach. Ta wersja MFC ma bezpośrednią pomoc techniczną dotyczącą tego nowego komunikatu przy użyciu makr ON_NOTIFY i ON_NOTIFY_RANGE. Zapoznaj się z dokumentacją produktu, aby uzyskać więcej informacji na temat tych makr.

## <a name="see-also"></a>Zobacz także

[Uwagi techniczne według numeru](../mfc/technical-notes-by-number.md)<br/>
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)
