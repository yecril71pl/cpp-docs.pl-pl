---
title: 'TN064: Wątkowość modelu Apartment w kontrolkach ActiveX'
ms.date: 11/04/2016
f1_keywords:
- vc.controls.activex
helpviewer_keywords:
- OLE controls [MFC], container support
- containers [MFC], multithreaded
- TN064 [MFC]
- multithread container [MFC]
- apartment model threading [MFC]
ms.assetid: b2ab4c88-6954-48e2-9a74-01d4a60df073
ms.openlocfilehash: 2c6b9dd3ed244f7169e5055eebe7a34e3345e841
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69513324"
---
# <a name="tn064-apartment-model-threading-in-activex-controls"></a>TN064: Wątkowość modelu Apartment w kontrolkach ActiveX

> [!NOTE]
>  Następująca Uwaga techniczna nie została zaktualizowana, ponieważ została najpierw uwzględniona w dokumentacji online. W związku z tym niektóre procedury i tematy mogą być nieaktualne lub nieprawidłowe. Aby uzyskać najnowsze informacje, zalecamy wyszukiwanie tematu zainteresowania w indeksie dokumentacji online.

Ta Uwaga techniczna wyjaśnia, jak włączyć wątkowość modelu Apartment w formancie ActiveX. Należy zauważyć, że wątkowość modelu Apartment jest obsługiwana tylko w C++ Visual wersji 4,2 lub nowszej.

## <a name="what-is-apartment-model-threading"></a>Co to jest wątkowość modelu Apartment

Model apartamentu to podejście do obsługi osadzonych obiektów, takich jak kontrolki ActiveX, w ramach aplikacji kontenera wielowątkowego. Mimo że aplikacja może mieć wiele wątków, każde wystąpienie osadzonego obiektu zostanie przypisane do jednej "Apartament", który będzie wykonywany tylko w jednym wątku. Innymi słowy, wszystkie wywołania do wystąpienia kontrolki będą miały miejsce w tym samym wątku.

Jednak różne wystąpienia tego samego typu kontrolki mogą być przypisane do różnych apartamentach. Tak więc, jeśli wiele wystąpień formantu współużytkuje dowolne dane (na przykład dane statyczne lub globalne), dostęp do tych udostępnionych danych będzie musiał być chroniony przez obiekt synchronizacji, taki jak Sekcja krytyczna.

Aby uzyskać szczegółowe informacje na temat modelu wątkowego Apartment, zobacz [procesy i wątki](/windows/win32/ProcThread/processes-and-threads) w *odwołaniu OLE programisty*.

## <a name="why-support-apartment-model-threading"></a>Dlaczego warto obsługiwać wątkowość modelu Apartment

Kontrolki obsługujące wątkowość modelu Apartment mogą być używane w aplikacjach kontenera wielowątkowego, które obsługują również model Apartment. Jeśli nie włączysz wątkowości modelu apartamentu, będzie można ograniczyć potencjalny zestaw kontenerów, w których może być używany formant.

Włączenie wątkowości modelu Apartment jest łatwe w przypadku większości kontrolek, szczególnie w przypadku, gdy nie mają one danych udostępnionych.

## <a name="protecting-shared-data"></a>Ochrona udostępnionych danych

Jeśli kontrolka używa danych udostępnionych, takich jak statyczna zmienna członkowska, dostęp do tych danych powinien być chroniony za pomocą sekcji krytycznej, aby zapobiec modyfikowaniu danych w tym samym czasie przez więcej niż jeden wątek. Aby skonfigurować sekcję krytyczną dla tego celu, zadeklaruj statyczną zmienną składową klasy `CCriticalSection` w klasie formantu. Użyj funkcji `Unlock` i elementu członkowskiego tego obiektu sekcji krytycznej wszędzie tam, gdzie kod uzyskuje dostęp do udostępnionych danych. `Lock`

Rozważmy na przykład klasę kontrolki, która musi obsługiwać ciąg, który jest współużytkowany przez wszystkie wystąpienia. Ten ciąg może być obsługiwany w statycznej zmiennej składowej i chroniony przez sekcję krytyczną. Deklaracja klasy kontrolki będzie zawierać następujące elementy:

```
class CSampleCtrl : public COleControl
{
...
    static CString _strShared;
    static CCriticalSection _critSect;
};
```

Implementacja klasy obejmuje definicje dla następujących zmiennych:

```
int CString CSampleCtrl::_strShared;
CCriticalSection CSampleCtrl::_critSect;
```

Dostęp do `_strShared` statycznego elementu członkowskiego może następnie być chroniony przez sekcję krytyczną:

```
void CSampleCtrl::SomeMethod()
{
    _critSect.Lock();
if (_strShared.Empty())
    _strShared = "<text>";
    _critSect.Unlock();

...
}
```

## <a name="registering-an-apartment-model-aware-control"></a>Rejestrowanie kontrolki obsługującej model typu Apartment

Kontrolki obsługujące wątkowość modelu Apartment powinny wskazywać tę możliwość w rejestrze, dodając nazwaną wartość "ThreadingModel" z wartością "Apartment" w wpisie rejestru identyfikatora klasy pod *identyfikatorem klasy* \\  **Klucz InprocServer32** . Aby spowodować automatyczne zarejestrowanie tego klucza dla formantu, należy przekazać flagę *afxRegApartmentThreading* w szóstym parametrze do `AfxOleRegisterControlClass`:

```
BOOL CSampleCtrl::CSampleCtrlFactory::UpdateRegistry(BOOL bRegister)
{
    if (bRegister)
    return AfxOleRegisterControlClass(
    AfxGetInstanceHandle(),
    m_clsid,
    m_lpszProgID,
    IDS_SAMPLE,
    IDB_SAMPLE,
    afxRegApartmentThreading,
    _dwSampleOleMisc,
    _tlid,
    _wVerMajor,
    _wVerMinor);

else
    return AfxOleUnregisterClass(m_clsid,
    m_lpszProgID);

}
```

Jeśli projekt kontrolki został wygenerowany przez ControlWizard w Visual C++ w wersji 4,1 lub nowszej, ta flaga będzie już obecna w kodzie. Nie są wymagane żadne zmiany, aby zarejestrować model wątkowości.

Jeśli projekt został wygenerowany przez wcześniejszą wersję programu ControlWizard, istniejący kod będzie miał wartość logiczną jako szósty parametr. Jeśli istniejący parametr ma wartość TRUE, zmień go na *afxRegInsertable | afxRegApartmentThreading*. Jeśli istniejący parametr ma wartość FALSE, zmień go na *afxRegApartmentThreading*.

Jeśli formant nie jest zgodny z regułami dla wątków modelu Apartment, nie należy przekazywać *afxRegApartmentThreading* w tym parametrze.

## <a name="see-also"></a>Zobacz także

[Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)<br/>
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)
