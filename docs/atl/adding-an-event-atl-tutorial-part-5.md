---
title: Dodawanie zdarzenia (ALT — Samouczek, część 5)
ms.custom: get-started-article
ms.date: 09/27/2018
ms.assetid: 2de12022-3148-4ce3-8606-8a9d4274f0e9
ms.openlocfilehash: c9a7c6f38a2f47ec808081e440a200737ad1928a
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127577"
---
# <a name="adding-an-event-atl-tutorial-part-5"></a>Dodawanie zdarzenia (ALT — Samouczek, część 5)

W tym kroku dodasz `ClickIn` i zdarzenie `ClickOut` do formantu ATL. Jeśli użytkownik kliknie na zewnątrz i `ClickOut`, zostanie wyzwolone zdarzenie `ClickIn`. Zadania umożliwiające dodanie zdarzenia są następujące:

- Dodawanie `ClickIn` i `ClickOut` metod

- Generowanie biblioteki typów

- Implementowanie interfejsów punktu połączenia

## <a name="adding-the-clickin-and-clickout-methods"></a>Dodawanie metod klikania i ClickOut

Po utworzeniu kontrolki ATL w kroku 2, należy zaznaczyć pole wyboru **punkty połączenia** . W pliku wielokąt. idl został utworzony interfejs `_IPolyCtlEvents`. Należy pamiętać, że nazwa interfejsu zaczyna się od znaku podkreślenia. Jest to Konwencja wskazująca, że interfejs jest interfejsem wewnętrznym. W ten sposób programy, które umożliwiają przeglądanie obiektów COM, mogą nie wyświetlać interfejsu użytkownika. Należy również zauważyć, że wybranie **punktów połączenia** dodaliśmy następujący wiersz w pliku wielokąt. idl, aby wskazać, że `_IPolyCtlEvents` jest domyślnym interfejsem źródłowym:

`[default, source] dispinterface _IPolyCtlEvents;`

Atrybut source wskazuje, że formant jest źródłem powiadomień, więc wywoła ten interfejs w kontenerze.

Teraz Dodaj `ClickIn` i `ClickOut` metody do interfejsu `_IPolyCtlEvents`.

### <a name="to-add-the-clickin-and-clickout-methods"></a>Aby dodać metody klikania i ClickOut

1. W **Eksplorator rozwiązań**Otwórz wielokąt. idl i Dodaj następujący kod w obszarze `methods:` w deklaracji `dispInterface_IPolyCtlEvents` biblioteki PolygonLib:

    ```cpp
   [id(1), helpstring("method ClickIn")] void ClickIn([in] LONG x,[in] LONG y);
   [id(2), helpstring("method ClickOut")] void ClickOut([in] LONG x,[in] LONG y);
    ```

Metody `ClickIn` i `ClickOut` przyjmują współrzędne x i y klikniętego punktu jako parametry.

## <a name="generating-the-type-library"></a>Generowanie biblioteki typów

Wygeneruj bibliotekę typów w tym momencie, ponieważ projekt będzie używać jej do uzyskiwania informacji potrzebnych do konstruowania interfejsu punktu połączenia i interfejsu kontenera punktu połączenia dla kontrolki.

### <a name="to-generate-the-type-library"></a>Aby wygenerować bibliotekę typów

1. Ponownie skompiluj projekt.

     — lub —

1. Kliknij prawym przyciskiem myszy plik wielokąta. idl w **Eksplorator rozwiązań** i kliknij polecenie **Kompiluj** w menu skrótów.

Spowoduje to utworzenie wielokąta pliku TLB, który jest biblioteką typów. Plik wielokąt. tlb nie jest widoczny w **Eksplorator rozwiązań**, ponieważ jest plikiem binarnym i nie można go wyświetlać ani edytować bezpośrednio.

## <a name="implementing-the-connection-point-interfaces"></a>Implementowanie interfejsów punktu połączenia

Implementowanie interfejsu punktu połączenia i interfejsu kontenera punktu połączenia dla kontrolki. W modelu COM zdarzenia są implementowane za pomocą mechanizmu punktów połączenia. Aby odbierać zdarzenia z obiektu COM, kontener ustanawia doradcę połączenie z punktem połączenia, który implementuje obiekt COM. Ponieważ obiekt COM może mieć wiele punktów połączenia, obiekt COM również implementuje interfejs kontenera punktu połączenia. Za pomocą tego interfejsu kontener może określić, które punkty połączenia są obsługiwane.

Interfejs implementujący punkt połączenia nosi nazwę `IConnectionPoint`, a interfejs implementujący kontener punktu połączenia jest nazywany `IConnectionPointContainer`.

Aby pomóc w zaimplementowaniu `IConnectionPoint`, użyj Kreatora implementacji punktu połączenia. Ten Kreator generuje interfejs `IConnectionPoint`, odczytując bibliotekę typów i implementując funkcję dla każdego zdarzenia, które może zostać wyzwolone.

### <a name="to-implement-the-connection-points"></a>Aby zaimplementować punkty połączenia

1. W **Eksplorator rozwiązań**Otwórz _IPolyCtlEvents_CP. h i Dodaj następujący kod do instrukcji `public:` w klasie `CProxy_IPolyCtlEvents`:

    ```cpp
    VOID Fire_ClickIn(LONG x, LONG y)
    {
        T* pT = static_cast<T*>(this);
        int nConnectionIndex;
        CComVariant* pvars = new CComVariant[2];
        int nConnections = m_vec.GetSize();

        for (nConnectionIndex = 0; nConnectionIndex < nConnections; nConnectionIndex++)
        {
            pT->Lock();
            CComPtr<IUnknown> sp = m_vec.GetAt(nConnectionIndex);
            pT->Unlock();
            IDispatch* pDispatch = reinterpret_cast<IDispatch*>(sp.p);
            if (pDispatch != NULL)
            {
                pvars[1].vt = VT_I4;
                pvars[1].lVal = x;
                pvars[0].vt = VT_I4;
                pvars[0].lVal = y;
                DISPPARAMS disp = { pvars, NULL, 2, 0 };
                pDispatch->Invoke(0x1, IID_NULL, LOCALE_USER_DEFAULT, DISPATCH_METHOD, &disp, NULL, NULL, NULL);
            }
        }
        delete[] pvars;

    }
    VOID Fire_ClickOut(LONG x, LONG y)
    {
        T* pT = static_cast<T*>(this);
        int nConnectionIndex;
        CComVariant* pvars = new CComVariant[2];
        int nConnections = m_vec.GetSize();

        for (nConnectionIndex = 0; nConnectionIndex < nConnections; nConnectionIndex++)
        {
            pT->Lock();
            CComPtr<IUnknown> sp = m_vec.GetAt(nConnectionIndex);
            pT->Unlock();
            IDispatch* pDispatch = reinterpret_cast<IDispatch*>(sp.p);
            if (pDispatch != NULL)
            {
                pvars[1].vt = VT_I4;
                pvars[1].lVal = x;
                pvars[0].vt = VT_I4;
                pvars[0].lVal = y;
                DISPPARAMS disp = { pvars, NULL, 2, 0 };
                pDispatch->Invoke(0x2, IID_NULL, LOCALE_USER_DEFAULT, DISPATCH_METHOD, &disp, NULL, NULL, NULL);
            }
        }
        delete[] pvars;

    }
    ```

Zobaczysz, że ten plik ma klasę o nazwie `CProxy_IPolyCtlEvents`, która pochodzi z `IConnectionPointImpl`. _IPolyCtlEvents_CP. h definiuje teraz dwie metody `Fire_ClickIn` i `Fire_ClickOut`, które przyjmują dwa parametry współrzędnych. Te metody są wywoływane, gdy chcesz uruchomić zdarzenie z formantu.

Po wybraniu opcji sterowanie z opcjami **punkty połączenia** zostanie wygenerowany plik _IPolyCtlEvents_CP. h. Dodano również `CProxy_PolyEvents` i `IConnectionPointContainerImpl` do listy dziedziczenia dla wielu kontrolek i `IConnectionPointContainer` uwidocznione przez dodanie odpowiednich wpisów do mapy COM.

Zakończono implementowanie kodu w celu obsługi zdarzeń. Teraz możesz dodać jakiś kod, aby wyzwolić zdarzenia w odpowiednim momencie. Pamiętaj, że po kliknięciu lewym przyciskiem myszy w kontrolce zostanie wyzwolone zdarzenie `ClickIn` lub `ClickOut`. Aby dowiedzieć się, kiedy użytkownik kliknie przycisk, Dodaj procedurę obsługi dla komunikatu `WM_LBUTTONDOWN`.

### <a name="to-add-a-handler-for-the-wm_lbuttondown-message"></a>Aby dodać procedurę obsługi dla komunikatu WM_LBUTTONDOWN

1. W **Widok klasy**kliknij prawym przyciskiem myszy klasę `CPolyCtl` i kliknij polecenie **Właściwości** w menu skrótów.

1. W oknie **Właściwości** kliknij ikonę **komunikaty** , a następnie kliknij pozycję `WM_LBUTTONDOWN` z listy po lewej stronie.

1. Z wyświetlonej listy rozwijanej kliknij pozycję **\<dodaj > OnLButtonDown**. Deklaracja obsługi `OnLButtonDown` zostanie dodana do PolyCtl. h, a implementacja programu obsługi zostanie dodana do PolyCtl. cpp.

Następnie zmodyfikuj procedurę obsługi.

### <a name="to-modify-the-onlbuttondown-method"></a>Aby zmodyfikować metodę OnLButtonDown

1. Zmień kod, który obejmuje metodę `OnLButtonDown` w PolyCtl. cpp (usunięcie dowolnego kodu umieszczonego przez kreatora) w taki sposób, aby wyglądał następująco:

    [!code-cpp[NVC_ATL_Windowing#57](../atl/codesnippet/cpp/adding-an-event-atl-tutorial-part-5_2.cpp)]

Ten kod wykorzystuje punkty obliczone w funkcji `OnDraw`, aby utworzyć region, który wykrywa kliknięcia myszą przez użytkownika z wywołaniem do `PtInRegion`.

Parametr *uMsg* jest identyfikatorem obsługiwanego komunikatu systemu Windows. Dzięki temu można mieć jedną funkcję, która obsługuje zakres komunikatów. Parametry *wParam* i *lParam* są standardowymi wartościami komunikatów, które są obsługiwane. Parametr *bHandled* pozwala określić, czy funkcja obsłuży komunikat, czy nie. Domyślnie wartość jest równa TRUE, aby wskazać, że funkcja obsłuży komunikat, ale można ją ustawić na wartość FALSE. Spowoduje to, że ATL będzie kontynuował wyszukiwanie kolejnej funkcji obsługi komunikatów do wysłania wiadomości.

## <a name="building-and-testing-the-control"></a>Kompilowanie i testowanie kontrolki

Wypróbuj teraz Twoje zdarzenia. Skompiluj formant i ponownie uruchom kontener testów kontrolki ActiveX. Tym razem Wyświetl okno Dziennik zdarzeń. Aby skierować zdarzenia do okna danych wyjściowych, kliknij pozycję **Rejestrowanie** w menu **Opcje** i wybierz polecenie **Rejestruj do okna danych wyjściowych**. Wstaw kontrolkę i spróbuj kliknąć w oknie. Należy pamiętać, że `ClickIn` jest uruchamiany po kliknięciu w obrębie wypełnionego wielokąta, a `ClickOut` jest uruchamiany po kliknięciu poza nim.

Następnie dodasz stronę właściwości.

[Wróć do kroku 4](../atl/changing-the-drawing-code-atl-tutorial-part-4.md) &#124; [w kroku 6](../atl/adding-a-property-page-atl-tutorial-part-6.md)

## <a name="see-also"></a>Zobacz też

[Samouczek](../atl/active-template-library-atl-tutorial.md)
