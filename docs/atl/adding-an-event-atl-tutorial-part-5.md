---
title: Dodawanie zdarzenia (ALT — Samouczek, część 5)
ms.custom: get-started-article
ms.date: 09/27/2018
ms.assetid: 2de12022-3148-4ce3-8606-8a9d4274f0e9
ms.openlocfilehash: 4576af12f73e907fa8826ad71185a42ed9b9308e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50643045"
---
# <a name="adding-an-event-atl-tutorial-part-5"></a>Dodawanie zdarzenia (ALT — Samouczek, część 5)

W tym kroku dodasz `ClickIn` i `ClickOut` zdarzeń do formantu biblioteki ATL. Zostanie uruchomiony `ClickIn` zdarzeń, jeśli użytkownik kliknie w ramach wielokąta i fire `ClickOut` Jeśli użytkownik kliknie poza. Dostępne są następujące zadania, aby dodać zdarzenie:

- Dodawanie `ClickIn` i `ClickOut` metody

- Generowanie biblioteki typów

- Implementacja interfejsów punktu połączenia

## <a name="adding-the-clickin-and-clickout-methods"></a>Dodawanie metody clickin — i ClickOut

Gdy kontrolka ATL jest utworzony w kroku 2, wybrania **punkty połączenia** pole wyboru. Spowodowało to `_IPolyCtlEvents` interfejsu w pliku Polygon.idl. Pamiętaj, że nazwa interfejsu, który rozpoczyna się od znaku podkreślenia. Jest to Konwencji, aby wskazać, że interfejs jest wewnętrzny. W związku z tym wybrać programy, które umożliwiają przeglądanie obiektów COM nie wyświetlić interfejs użytkownika. Należy również zauważyć, że wybranie **punkty połączenia** dodano następujący wiersz w pliku Polygon.idl, aby wskazać, że `_IPolyCtlEvents` jest domyślnym interfejsie źródła:

`[default, source] dispinterface _IPolyCtlEvents;`

Atrybut źródłowy wskazuje, czy kontrolka jest źródło powiadomienia, dzięki czemu będzie on wywołać ten interfejs w kontenerze.

Teraz Dodaj `ClickIn` i `ClickOut` metody `_IPolyCtlEvents` interfejsu.

### <a name="to-add-the-clickin-and-clickout-methods"></a>Aby dodać metody clickin — i ClickOut

1. W **Eksploratora rozwiązań**, otwórz Polygon.idl i Dodaj następujący kod w obszarze `methods:` w `dispInterface_IPolyCtlEvents` deklaracji biblioteki PolygonLib:

    ```cpp
   [id(1), helpstring("method ClickIn")] void ClickIn([in] LONG x,[in] LONG y);
   [id(2), helpstring("method ClickOut")] void ClickOut([in] LONG x,[in] LONG y);
    ```

`ClickIn` i `ClickOut` metody podjęcie x i współrzędne y punktu kliknięto jako parametry.

## <a name="generating-the-type-library"></a>Generowanie biblioteki typów

Generuj bibliotekę typów w tym momencie, ponieważ projekt będzie używać go do uzyskania informacji wymaganych do utworzenia punktu połączenia i interfejsem kontenera punktu połączenia dla kontrolki.

### <a name="to-generate-the-type-library"></a>Aby wygenerować bibliotekę typów

1. Ponownie skompiluj projekt.

     —lub—

1. Kliknij prawym przyciskiem myszy plik Polygon.idl **Eksploratora rozwiązań** i kliknij przycisk **skompilować** w menu skrótów.

Spowoduje to utworzenie pliku Polygon.tlb, czyli bibliotece typu. Plik Polygon.tlb nie jest on widoczny **Eksploratora rozwiązań**, ponieważ ona jest plikiem binarnym i nie można wyświetlić lub edytować bezpośrednio.

## <a name="implementing-the-connection-point-interfaces"></a>Implementacja interfejsów punktu połączenia

Implementowanie interfejsu punktu połączenia oraz interfejs kontenera punktu połączenia dla kontrolki. W modelu COM zdarzenia są implementowane za pośrednictwem mechanizmu punkty połączenia. Aby odbierać zdarzenia z obiektem COM, kontener, ustanawia połączenie porad dotyczących punktu połączenia, który implementuje obiekt COM. Ponieważ obiekt COM może mieć wiele punktów połączenia, obiekt COM implementuje również interfejs kontenera punktu połączenia. Za pomocą tego interfejsu kontenera można określić punktów połączenia, które są obsługiwane.

Interfejs, który implementuje punkt połączenia jest nazywany `IConnectionPoint`, i wywoływany jest interfejs, który implementuje kontener punktu połączenia `IConnectionPointContainer`.

Pomagających w realizacji `IConnectionPoint`, użyje Kreator implementacji punktu połączenia. Ten kreator generuje `IConnectionPoint` interfejsu, odczytując biblioteki typu i implementacja funkcji dla każdego zdarzenia, które mogą być uruchamiane.

### <a name="to-implement-the-connection-points"></a>Aby zaimplementować punkty połączenia

1. W **Eksploratora rozwiązań**, otwórz _IPolyCtlEvents_CP.h i Dodaj następujący kod w obszarze `public:` instrukcji w `CProxy_IPolyCtlEvents` klasy:

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

Zobaczysz, że ten plik zawiera klasę o nazwie `CProxy_IPolyCtlEvents` który pochodzi od klasy `IConnectionPointImpl`. _IPolyCtlEvents_CP.h teraz definiuje dwie metody `Fire_ClickIn` i `Fire_ClickOut`, które przyjmują dwa parametry współrzędnych. Możesz wywołać te metody, jeśli chcesz wyzwolić zdarzenie z usługi kontroli.

Tworząc kontrolki z **punkty połączenia** opcja jest zaznaczona, plik _IPolyCtlEvents_CP.h został wygenerowany dla Ciebie. Dodano również `CProxy_PolyEvents` i `IConnectionPointContainerImpl` do kontroli nad wieloma listy dziedziczenia i ujawnione `IConnectionPointContainer` dla Ciebie, dodając odpowiednie wpisy do mapy COM.

Po zakończeniu wdrażania kodu do obsługi zdarzeń. Teraz Dodaj kod wyzwolenie zdarzenia w odpowiedniej chwili. Należy pamiętać, że zamierzasz uruchomić `ClickIn` lub `ClickOut` zdarzenie, kiedy użytkownik kliknie przycisk myszy po lewej stronie w formancie. Aby dowiedzieć się, gdy użytkownik kliknie przycisk, Dodaj program obsługi `WM_LBUTTONDOWN` wiadomości.

### <a name="to-add-a-handler-for-the-wmlbuttondown-message"></a>Aby dodać program obsługi komunikatów WM_LBUTTONDOWN

1. W **Widok klas**, kliknij prawym przyciskiem myszy `CPolyCtl` klasy, a następnie kliknij przycisk **właściwości** w menu skrótów.

1. W **właściwości** okna, kliknij przycisk **wiadomości** ikonę, a następnie kliknij przycisk `WM_LBUTTONDOWN` z listy po lewej stronie.

1. Z listy rozwijanej, która zostanie wyświetlona, kliknij przycisk  **\<Dodaj > onlbuttondown —**. `OnLButtonDown` Deklaracja procedury obsługi, które zostaną dodane do PolyCtl.h i implementację obsługi zostanie dodany do PolyCtl.cpp.

Następnie zmodyfikuj program obsługi.

### <a name="to-modify-the-onlbuttondown-method"></a>Aby zmodyfikować onlbuttondown — metoda

1. Zmień kod, który składa się z `OnLButtonDown` metody w PolyCtl.cpp (usuwanie każdy kod umieszczony przez kreatora), aby wygląda następująco:

    [!code-cpp[NVC_ATL_Windowing#57](../atl/codesnippet/cpp/adding-an-event-atl-tutorial-part-5_2.cpp)]

To sprawia, że kod użycie punktów obliczane w `OnDraw` funkcji, aby utworzyć obszar, który wykrywa kliknięcia myszą przez użytkownika z wywołaniem `PtInRegion`.

*UMsg* parametr jest identyfikator komunikatu Windows jest obsługiwany. Dzięki temu można mieć jedną funkcję, która obsługuje szeroką gamę wiadomości. *WParam* i *lParam* są standardowe wartości dla komunikatu przetwarzanego przez parametry. Parametr *bHandled* pozwala określić, czy funkcja obsługi wiadomości. Domyślnie wartość jest równa TRUE wskazują, że funkcja obsługi wiadomości, ale zostanie ustawiona na wartość FALSE. Spowoduje to ATL kontynuować wyszukiwanie innej funkcji obsługi wiadomości, można wysłać wiadomości do.

## <a name="building-and-testing-the-control"></a>Tworzenie i testowanie formantu

Wypróbuj teraz zdarzeń. Kompiluj wersję i ponownie uruchomić kontener testu kontrolki ActiveX. Tym razem wyświetlić okno Dziennik zdarzeń. Aby kierowanie zdarzeń w oknie danych wyjściowych, kliknij przycisk **rejestrowania** z **opcje** menu, a następnie wybierz **dziennika w oknie danych wyjściowych**. Wstaw kontrolkę i spróbuj kliknąć w oknie. Należy pamiętać, że `ClickIn` jest wywoływane po kliknięciu w ramach wypełniony wielokąt i `ClickOut` uruchamiane, gdy klikniesz poza nią.

Następnie można dodać strony właściwości.

[Wróć do kroku 4](../atl/changing-the-drawing-code-atl-tutorial-part-4.md) &#124; [do kroku 6](../atl/adding-a-property-page-atl-tutorial-part-6.md)

## <a name="see-also"></a>Zobacz też

[Samouczek](../atl/active-template-library-atl-tutorial.md)
