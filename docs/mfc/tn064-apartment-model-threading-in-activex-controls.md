---
title: 'TN064: Model wątkowości w kontrolkach ActiveX typu apartment'
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
ms.openlocfilehash: d6f02b2106693226f6380e935a54e04e10d5b4f8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62351829"
---
# <a name="tn064-apartment-model-threading-in-activex-controls"></a>TN064: Model wątkowości w kontrolkach ActiveX typu apartment

> [!NOTE]
>  Następująca uwaga techniczna nie został zaktualizowany od pierwszego uwzględnienia jej w dokumentacji online. W rezultacie niektóre procedury i tematy może być nieaktualne lub niepoprawne. Najnowsze informacje zaleca się wyszukać temat w indeksie dokumentacji online.

Ta uwaga techniczna wyjaśnia, jak włączyć model wątkowości typu apartment w kontrolce ActiveX. Należy pamiętać, że model wątkowości typu apartment jest obsługiwana tylko w wersjach Visual C++ 4.2 i nowsze.

## <a name="what-is-apartment-model-threading"></a>Co to jest Model wątkowości typu Apartment

Modelu typu apartment to podejście do obsługi osadzonych obiektów, takich jak kontrolki ActiveX, w ramach aplikacji wielowątkowych kontenera. Mimo że aplikacja może mieć wiele wątków, każde wystąpienie osadzonego obiektu zostanie przypisany do jednego "apartament,", które zostaną wykonane zgodnie z tylko jednego wątku. Innymi słowy w tym samym wątku nastąpi wszystkie wywołania do wystąpienia formantu.

Jednak różnymi wystąpieniami tego samego typu formantu może być przypisana do różnych apartamentach. Tak wiele wystąpień kontrolki udostępniono wszystkie dane w typowych (na przykład dane statyczne lub globalny), dostęp do tych danych udostępnionych będzie potrzebne ma być chroniona za pomocą obiektu synchronizacji, takie jak sekcję krytyczną.

Aby uzyskać szczegółowe informacje dotyczące typu apartment model wątkowości, zobacz [procesy i wątki](/windows/desktop/ProcThread/processes-and-threads) w *OLE Podręcznik programisty*.

## <a name="why-support-apartment-model-threading"></a>Dlaczego obsługuje Model wątkowości typu Apartment

Formanty, które obsługują model wątkowości typu apartment może służyć w aplikacjach wielowątkowych kontenera, które obsługują także modelu typu apartment. Jeśli nie zostanie włączone, model wątkowości typu apartment, będzie ograniczyć potencjalne zestaw kontenerów, w których można użyć formantu.

Włączanie model wątkowości typu apartment jest bardzo proste dla większości kontrolek, szczególnie w przypadku, gdy mają one niewielkiego lub żadnego udostępnionych danych.

## <a name="protecting-shared-data"></a>Ochrona udostępnionych danych

Jeśli kontroli nad używa danych udostępnionych, takich jak zmienną statyczną składową dostęp do, dane powinny być chronione przy użyciu sekcję krytyczną, aby uniemożliwić modyfikowanie danych w tym samym czasie więcej niż jeden wątek. Aby skonfigurować sekcję krytyczną, w tym celu, należy zadeklarować zmienną statyczną składową klasy `CCriticalSection` klasy formantu. Użyj `Lock` i `Unlock` funkcje Członkowskie krytyczne informacje przedstawione w tej sekcji obiekt wszędzie tam, gdzie Twój kod uzyskuje dostęp do udostępnionych danych.

Należy wziąć pod uwagę, na przykład klasa kontrolki, która musi być ciąg, który jest współużytkowany przez wszystkie wystąpienia. Ten ciąg może przechowywane w zmiennej członka statycznego i chronione przez sekcję krytyczną. Deklaracja klasy kontrolki będzie zawierać następujące informacje:

```
class CSampleCtrl : public COleControl
{
...
    static CString _strShared;
    static CCriticalSection _critSect;
};
```

Implementacja klasy zawierałoby definicje dla tych zmiennych:

```
int CString CSampleCtrl::_strShared;
CCriticalSection CSampleCtrl::_critSect;
```

Dostęp do `_strShared` statyczny element członkowski, następnie mogą być chronione przez sekcję krytyczną:

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

## <a name="registering-an-apartment-model-aware-control"></a>Rejestrowanie kontrolkę typu Apartment-Model-Aware

Formanty, które obsługują model wątkowości typu apartment powinna być widoczna tej możliwości w rejestrze, dodając nazwanej wartości "ThreadingModel" o wartości "Apartamentu" w ich klasy identyfikator wpisu rejestru *identyfikator klasy* \\ **InprocServer32** klucza. Aby spowodować, że ten klucz, aby automatycznie rejestrowane dla kontrolki, należy przekazać *afxRegApartmentThreading* flagi w parametrze szóstego `AfxOleRegisterControlClass`:

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

Jeśli projekt kontroli został wygenerowany przez ControlWizard w Visual C++ w wersji 4.1 lub nowszym, ta flaga będą już obecne w kodzie. Żadne zmiany nie są niezbędne zarejestrować model wątkowości.

Jeśli projekt został wygenerowany przez starszą wersję ControlWizard, istniejącego kodu mają wartość typu Boolean jako szóstego parametru. Jeśli istniejący parametr ma wartość PRAWDA, zmień ją na *afxRegInsertable | afxRegApartmentThreading*. Jeśli istniejący parametr ma wartość FALSE, zmień ją na *afxRegApartmentThreading*.

Jeśli formant nie jest zgodna z zasadami model wątkowości typu apartment, nie należy przekazać *afxRegApartmentThreading* w tym parametrze.

## <a name="see-also"></a>Zobacz także

[Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)<br/>
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)
