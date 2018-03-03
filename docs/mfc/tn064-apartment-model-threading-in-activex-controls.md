---
title: "TN064: Model typu Apartment wątkowości w formantach ActiveX | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.controls.activex
dev_langs:
- C++
helpviewer_keywords:
- OLE controls [MFC], container support
- containers [MFC], multithreaded
- TN064 [MFC]
- multithread container [MFC]
- apartment model threading [MFC]
ms.assetid: b2ab4c88-6954-48e2-9a74-01d4a60df073
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 07730d6c078dcc8fcd7ea1406f8cff6f665c9919
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="tn064-apartment-model-threading-in-activex-controls"></a>TN064: model wątkowości typu apartment w kontrolkach ActiveX
> [!NOTE]
>  Poniższe uwagi techniczne nie został zaktualizowany, ponieważ została ona uwzględniona w dokumentacji online. W związku z tym niektóre procedury i tematy mogą być nieaktualne lub niepoprawne. Najnowsze informacje zalecane jest, możesz wyszukać temat odsetek w indeksie dokumentacji online.  
  
 Ta uwaga techniczna wyjaśniono, jak włączyć apartamentu model wątkowości w formancie ActiveX. Należy pamiętać, że apartamentu model wątkowości jest obsługiwana tylko w Visual C++ w wersji 4.2 lub nowszej.  
  
## <a name="what-is-apartment-model-threading"></a>Co to jest apartamentu Model wątkowości  
 Modelu typu apartment jest rozwiązanie do obsługi osadzonych obiektów, takich jak kontrolki ActiveX w aplikacji wielowątkowych kontenera. Mimo że aplikacja może mieć wiele wątków, każde wystąpienie obiektu osadzonego zostanie przypisana do jednego "apartament,", który zostanie wykonany w tylko jednym wątku. Innymi słowy w tym samym wątku nastąpi wszystkie wywołania do wystąpienia formantu.  
  
 Jednak różnych wystąpień tego samego typu formantu mogły zostać przypisane do różnych apartamentach. Tak wiele wystąpień formantu udostępniania danych wspólną (na przykład dane statyczne lub globalnego), dostęp do tych danych udostępnionych będzie konieczne mają być chronione przez obiekt synchronizacji, takie jak sekcja krytyczna.  
  
 Aby uzyskać szczegółowe informacje o modelu wątków, zobacz [procesów i wątków](http://msdn.microsoft.com/library/windows/desktop/ms684841) w *OLE Podręcznik programisty*.  
  
## <a name="why-support-apartment-model-threading"></a>Dlaczego obsługuje apartamentu Model wątkowości  
 Formanty, obsługujących wątkowości typu apartment modelu mogą być używane w aplikacjach wielowątkowych kontenera, które obsługują także modelu typu apartment. Jeśli nie zostanie włączone, apartamentu model wątkowości, ograniczy zestawu potencjalnych kontenerów, w których można użyć formantu.  
  
 Włączanie apartamentu model wątkowości jest bardzo proste dla większości formantów, zwłaszcza w przypadku, gdy mają one żadnych danych udostępnionych.  
  
## <a name="protecting-shared-data"></a>Ochrona danych udostępnionych  
 Jeśli formantu używa udostępnionych danych, takich jak statycznym elementem członkowskim zmiennej, dostęp do czy dane powinny być chronione przy użyciu sekcja krytyczna, aby zapobiec modyfikowanie danych w tym samym czasie więcej niż jeden wątek. Aby skonfigurować sekcja krytyczna w tym celu, należy zadeklarować zmienną statyczny element członkowski klasy `CCriticalSection` klasy formantu. Użyj `Lock` i **Unlock** funkcji Członkowskich w tej sekcji krytycznych obiektów wszędzie tam, gdzie kod uzyskuje dostęp do współużytkowanych danych.  
  
 Na przykład, należy rozważyć klasy formantu, który musi być ciągiem, który jest współużytkowana przez wszystkie wystąpienia. Ten ciąg może przechowywane w zmiennej statyczny element członkowski i chronione sekcja krytyczna. Deklaracja klasy formantu będzie zawierać następujące informacje:  
  
```  
class CSampleCtrl : public COleControl  
{  
 ...  
    static CString _strShared;  
    static CCriticalSection _critSect;  
};  
```  
  
 Implementacja klasy to definicje dla tych zmiennych:  
  
```  
int CString CSampleCtrl::_strShared;  
CCriticalSection CSampleCtrl::_critSect;  
```  
  
 Dostęp do `_strShared` statyczny element członkowski następnie mogą być chronione przez sekcję krytycznych:  
  
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
  
## <a name="registering-an-apartment-model-aware-control"></a>Rejestrowania apartamentu modelu rozpoznają formantów  
 Formantów, które obsługują apartamentu model wątkowości powinny wskazywać tę funkcję w rejestrze, dodając wartość o nazwie "ThreadingModel" o wartości "Apartment" w ich klasy identyfikator wpisu rejestru *identyfikator klasy* \\ **InprocServer32** klucza. Aby spowodować, że ten klucz, aby być automatycznie rejestrowane dla formantu, należy przekazać `afxRegApartmentThreading` flagi w parametrze szóstego `AfxOleRegisterControlClass`:  
  
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
  
 Jeśli projekt kontroli został wygenerowany przez ControlWizard w programie Visual C++ wersji 4.1 lub nowszą, ta flaga zostanie utworzona w kodzie. Żadne zmiany są niezbędne zarejestrować model wątkowy.  
  
 Jeśli projekt został wygenerowany za pomocą starszej wersji ControlWizard, istniejący kod ma wartość logiczną jako szóstego parametru. Jeśli istniejący parametr ma wartość PRAWDA, zmień go na `afxRegInsertable | afxRegApartmentThreading`. Jeśli istniejący parametr ma wartość FALSE, zmień go na `afxRegApartmentThreading`.  
  
 Jeśli zasady apartamentu model wątkowości nie jest zgodna z formantu, należy nie przekazać `afxRegApartmentThreading` w tym parametrze.  
  
## <a name="see-also"></a>Zobacz też  
 [Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)   
 [Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)

