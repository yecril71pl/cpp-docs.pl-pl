---
title: 'TN064: model wątkowości typu apartment w kontrolkach ActiveX'
ms.date: 11/04/2016
helpviewer_keywords:
- OLE controls [MFC], container support
- containers [MFC], multithreaded
- TN064 [MFC]
- multithread container [MFC]
- apartment model threading [MFC]
ms.assetid: b2ab4c88-6954-48e2-9a74-01d4a60df073
ms.openlocfilehash: 0c6a42124b4b2b03ae7cd9277fa14d43eac7a2bb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366068"
---
# <a name="tn064-apartment-model-threading-in-activex-controls"></a>TN064: model wątkowości typu apartment w kontrolkach ActiveX

> [!NOTE]
> Następująca uwaga techniczna nie została zaktualizowana, ponieważ została po raz pierwszy uwzględniona w dokumentacji online. W rezultacie niektóre procedury i tematy mogą być nieaktualne lub nieprawidłowe. Aby uzyskać najnowsze informacje, zaleca się wyszukicie tematu interesującego w indeksie dokumentacji online.

W tej notatce technicznej wyjaśniono, jak włączyć gwintowanie modelu mieszkania w formancie ActiveX. Należy zauważyć, że wątki modelu apartamentu jest obsługiwany tylko w języku Visual C++ w wersji 4.2 lub nowszej.

## <a name="what-is-apartment-model-threading"></a>Co to jest model mieszkania wątki

Model apartamentu jest podejście do obsługi obiektów osadzonych, takich jak formanty ActiveX, w aplikacji kontenera wielowątkowego. Chociaż aplikacja może mieć wiele wątków, każde wystąpienie osadzonego obiektu zostanie przypisane do jednego "apartamentu", który zostanie wykonany tylko w jednym wątku. Innymi słowy wszystkie wywołania w wystąpieniu formantu będzie się w tym samym wątku.

Jednak różne wystąpienia tego samego typu kontroli mogą być przypisane do różnych mieszkań. Tak więc jeśli wiele wystąpień formantu współużytkuje wszystkie wspólne dane (na przykład dane statyczne lub globalne), dostęp do tych udostępnionych danych będzie musiał być chroniony przez obiekt synchronizacji, taki jak sekcja krytyczna.

Szczegółowe informacje na temat modelu gwintowania mieszkania można znaleźć w opisie [procesów i wątków](/windows/win32/ProcThread/processes-and-threads) w *referencji programisty OLE.*

## <a name="why-support-apartment-model-threading"></a>Dlaczego wsparcie model apartamentu wątki

Formanty obsługujące gwintowanie modelu mieszkania mogą być używane w aplikacjach kontenerów wielowątkowych, które obsługują również model apartamentu. Jeśli nie włączysz wątkowania modelu mieszkania, ograniczysz potencjalny zestaw kontenerów, w których można użyć formantu.

Włączanie wątków modelu mieszkania jest łatwe dla większości formantów, szczególnie jeśli mają one niewiele udostępnionych danych lub ich brak.

## <a name="protecting-shared-data"></a>Ochrona danych udostępnionych

Jeśli formant używa udostępnionych danych, takich jak zmienna statycznego elementu członkowskiego, dostęp do tych danych powinny być chronione za pomocą sekcji krytycznej, aby zapobiec więcej niż jeden wątek z modyfikowania danych w tym samym czasie. Aby skonfigurować sekcję krytyczną w tym celu, `CCriticalSection` zadeklarować statyczną zmienną elementu członkowskiego klasy w klasie formantu. Użyj `Lock` funkcji `Unlock` i członków tego obiektu sekcji krytycznej, gdziekolwiek kod uzyskuje dostęp do udostępnionych danych.

Rozważmy na przykład klasy kontroli, która musi obsługiwać ciąg, który jest współużytkowane przez wszystkie wystąpienia. Ten ciąg może być utrzymywany w statycznej zmiennej członkowskiej i chroniony przez sekcję krytyczną. Deklaracja klasy formantu będzie zawierać następujące elementy:

```cpp
class CSampleCtrl : public COleControl
{
...
    static CString _strShared;
    static CCriticalSection _critSect;
};
```

Implementacja dla klasy będzie zawierać definicje dla tych zmiennych:

```cpp
int CString CSampleCtrl::_strShared;
CCriticalSection CSampleCtrl::_critSect;
```

Dostęp do `_strShared` statycznego elementu członkowskiego może być chroniony przez sekcję krytyczną:

```cpp
void CSampleCtrl::SomeMethod()
{
    _critSect.Lock();
if (_strShared.Empty())
    _strShared = "<text>";
    _critSect.Unlock();

...
}
```

## <a name="registering-an-apartment-model-aware-control"></a>Rejestrowanie kontroli z uwzględnieniem modelu mieszkania

Formanty obsługujące wątki modelu mieszkania powinny wskazywać tę możliwość w rejestrze, dodając nazwaną wartość "ThreadingModel" o wartości "Apartment" w ich wpisu rejestru identyfikatora klasy w ramach *klucza klasy id*\\**InprocServer32.** Aby spowodować automatyczne zarejestrowanie tego klucza dla formantu, przekaż flagę *afxRegApartmentThreading* w szóstym parametrze do: `AfxOleRegisterControlClass`

```cpp
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

Jeśli projekt formantu został wygenerowany przez Formwizard w języku Visual C++ w wersji 4.1 lub nowszej, ta flaga będzie już obecna w kodzie. Żadne zmiany nie są wymagane do zarejestrowania modelu wątkowania.

Jeśli projekt został wygenerowany przez wcześniejszą wersję ControlWizard, istniejący kod będzie miał wartość logiczną jako szósty parametr. Jeśli istniejący parametr to TRUE, zmień go na *afxRegInsertable | afxRegApartmentThreading*. Jeśli istniejący parametr to FALSE, zmień go na *afxRegApartmentThreading*.

Jeśli formant nie jest zgodny z regułami wątkowania modelu mieszkania, nie należy przekazywać *afxRegApartmentThreading* w tym parametrze.

## <a name="see-also"></a>Zobacz też

[Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)<br/>
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)
