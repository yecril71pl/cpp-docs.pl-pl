---
title: Wątkowość i marshaling (C++/CX)
ms.date: 12/30/2016
f1_keywords:
- C4451
helpviewer_keywords:
- threading issues, C++/CX
- agility, C++/CX
- C++/CX, threading issues
ms.assetid: 83e9ca1d-5107-4194-ae6f-e01bd928c614
ms.openlocfilehash: 6b57366df5f466ffe49e4c0b46e05b1eed515535
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "82032489"
---
# <a name="threading-and-marshaling-ccx"></a>Wątkowość i marshaling (C++/CX)

W zdecydowanej większości przypadków wystąpienia klas środowiska wykonawczego systemu Windows, takich jak standardowe obiekty C++, są dostępne z dowolnego wątku. Takie klasy są określane jako "agile". Jednak niewielka liczba klas środowiska wykonawczego systemu Windows dostarczanych z systemem Windows nie jest elastyczna i musi być zużywana bardziej jak obiekty COM niż standardowe obiekty C++. Nie trzeba być ekspertem COM do korzystania z klas nieasmorodki, ale należy wziąć pod uwagę model wątków klasy i jego zachowanie organizowania. Ten artykuł zawiera tło i wskazówki dotyczące tych rzadkich scenariuszy, w których należy spożywać wystąpienie klasy nieaskładnikowej.

## <a name="threading-model-and-marshaling-behavior"></a>Model wątków i zachowanie organizowania

Klasa środowiska wykonawczego systemu Windows może obsługiwać równoczesny dostęp do wątków na różne sposoby, zgodnie z dwoma atrybutami, które są do niej stosowane:

- `ThreadingModel`atrybut może mieć jedną z wartości — STA, MTA lub `ThreadingModel` Both, zgodnie z definicją wyliczenia.

- `MarshallingBehavior`atrybut może mieć jedną z wartości — Agile, None `MarshallingType` lub Standard zgodnie z definicją wyliczenia.

Atrybut `ThreadingModel` określa, gdzie klasa jest ładowana po aktywacji: tylko w kontekście wątku interfejsu użytkownika (STA), tylko w kontekście wątku tła (MTA) lub w kontekście wątku, który tworzy obiekt (Oba). Wartości `MarshallingBehavior` atrybutów odnoszą się do zachowania obiektu w różnych kontekstach wątków; w większości przypadków nie trzeba szczegółowo rozumieć tych wartości.  Z klas, które są dostarczane przez interfejs API `ThreadingModel`systemu Windows, około 90 procent ma =Both i `MarshallingType`=Agile. Oznacza to, że mogą obsługiwać szczegóły gwintowania niskiego poziomu w sposób przejrzysty i wydajny.   Podczas tworzenia `ref new` klasy "agile", można wywołać metody na nim z głównego wątku aplikacji lub z jednego lub więcej wątków roboczych.  Innymi słowy, możesz użyć klasy agile — niezależnie od tego, czy jest dostarczana przez system Windows, czy przez inną firmę — z dowolnego miejsca w kodzie. Nie musisz się martwić o model wątków klasy lub zachowanie organizowania.

## <a name="consuming-windows-runtime-components"></a>Korzystanie ze składników środowiska wykonawczego systemu Windows

Podczas tworzenia aplikacji platformy uniwersalnej systemu Windows można wchodzić w interakcje ze składnikami agile i nieaskładliwymi. Podczas interakcji z nieztwawnych składników, może wystąpić następujące ostrzeżenie.

### <a name="compiler-warning-c4451-when-consuming-non-agile-classes"></a>Ostrzeżenie kompilatora C4451 podczas korzystania z klas niezwiązanych z agile

Z różnych powodów niektóre klasy nie mogą być zwinne. Jeśli uzyskujesz dostęp do wystąpień klas nieaskładnych zarówno z wątku interfejsu użytkownika, jak i wątku w tle, należy zachować szczególną ostrożność, aby zapewnić poprawne zachowanie w czasie wykonywania. Kompilator Microsoft C++ wydaje ostrzeżenia podczas tworzenia wystąpienia klasy nieaskuteczowej w aplikacji w zakresie globalnym lub deklarowania typu nieaskutecznego jako elementu członkowskiego klasy ref, która sama jest oznaczona jako agile.

Z klas niezwiązanych z agile najłatwiejsze `ThreadingModel`do `MarshallingType`czynienia z są te, które mają =Zarówno i = Standard.  Możesz sprawić, aby te klasy `Agile<T>` były zwinne tylko przy użyciu klasy pomocnika.   W poniższym przykładzie przedstawiono deklarację nieaskuteczny obiekt typu `Windows::Security::Credentials::UI::CredentialPickerOptions^`i ostrzeżenie kompilatora, który jest wystawiany w wyniku.

```

ref class MyOptions
    {
    public:
        property Windows::Security::Credentials::UI::CredentialPickerOptions^ Options

        {
            Windows::Security::Credentials::UI::CredentialPickerOptions^ get()
            {
                return _myOptions;
            }
        }
    private:
        Windows::Security::Credentials::UI::CredentialPickerOptions^ _myOptions;
    };
```

Oto ostrzeżenie, które zostało wydane:

> `Warning 1 warning C4451: 'Platform::Agile<T>::_object' : Usage of ref class 'Windows::Security::Credentials::UI::CredentialPickerOptions' inside this context can lead to invalid marshaling of object across contexts. Consider using 'Platform::Agile<Windows::Security::Credentials::UI::CredentialPickerOptions>' instead`

Po dodaniu odwołania — w zakresie członkowskim lub zakresie globalnym — do obiektu, który ma zachowanie organizowania "Standard", `Platform::Agile<T>`kompilator wydaje ostrzeżenie, które zaleca zawijanie typu w : `Consider using 'Platform::Agile<Windows::Security::Credentials::UI::CredentialPickerOptions>' instead` Jeśli używasz, `Agile<T>`można korzystać z klasy, jak można innych agile klasy. Zastosowanie `Platform::Agile<T>` w następujących okolicznościach:

- Zmienna niezwiązane jest zadeklarowana w zakresie globalnym.

- Zmienna nieaskładnikowa jest zadeklarowana w zakresie klasy i istnieje szansa, że użycie kodu może przemycić wskaźnik — oznacza to, że użyj go w innym mieszkaniu bez prawidłowego organizowania.

Jeśli żaden z tych warunków nie ma zastosowania, można oznaczyć klasę zawierającą jako nieaskusną. Innymi słowy należy bezpośrednio przechowywać nieaskładne obiekty tylko w klasach niezwiązanych z\<agile i przytrzymaj nieztwychwłaste obiekty za pośrednictwem platformy::Agile T> w klasach agile.

W poniższym przykładzie `Agile<T>` pokazano, jak używać, dzięki czemu można bezpiecznie zignorować ostrzeżenie.

```

#include <agile.h>
ref class MyOptions
    {
    public:
        property Windows::Security::Credentials::UI::CredentialPickerOptions^ Options

        {
            Windows::Security::Credentials::UI::CredentialPickerOptions^ get()
            {
                return m_myOptions.Get();
            }
        }
    private:
        Platform::Agile<Windows::Security::Credentials::UI::CredentialPickerOptions^> m_myOptions;

    };
```

Należy `Agile` zauważyć, że nie można przekazać jako wartość zwracana lub parametr w klasie ref. Metoda `Agile<T>::Get()` zwraca dojście do obiektu (^), który można przekazać przez interfejs binarny aplikacji (ABI) w metodzie publicznej lub właściwości.

Podczas tworzenia odwołania do klasy środowiska wykonawczego systemu Windows w prochorze, która ma zachowanie organizowania "Brak", kompilator `Platform::Agile<T>`wydaje ostrzeżenie C4451, ale nie sugeruje, że należy rozważyć użycie .  Kompilator nie może zaoferować żadnej pomocy poza tym ostrzeżeniem, więc jest odpowiedzialny za użycie klasy poprawnie i upewnij się, że kod wywołuje składniki STA tylko z wątku interfejsu użytkownika i składników MTA tylko z wątku w tle.

## <a name="authoring-agile-windows-runtime-components"></a>Tworzenie składników elastycznego środowiska wykonawczego systemu Windows

Po zdefiniowaniu klasy ref w języku C++/CX jest ona domyślnie `ThreadingModel`elastyczna `MarshallingType`— oznacza to, że ma =Obie i =Agile.  Jeśli używasz biblioteki szablonów Środowiska Wykonawczego systemu Windows W++, możesz `FtmBase`sprawić, by `FreeThreadedMarshaller`klasa była elastyczna, czerpiąc z programu , który używa pliku .  Jeśli autor klasy, `ThreadingModel`która ma `ThreadingModel`=Obu lub = MTA, upewnij się, że klasa jest bezpieczna dla wątków.

Można zmodyfikować model wątków i zachowanie organizowania klasy ref. Jednak jeśli wniesiesz zmiany, które sprawiają, że klasa nie jest zwinna, należy zrozumieć implikacje, które są skojarzone z tymi zmianami.

W poniższym przykładzie `MarshalingBehavior` `ThreadingModel` pokazano, jak zastosować i atrybuty do klasy środowiska wykonawczego w bibliotece klas środowiska wykonawczego systemu Windows. Gdy aplikacja używa biblioteki DLL `ref new` i używa `MySTAClass` słowa kluczowego, aby aktywować obiekt klasy, obiekt jest aktywowany w mieszkaniu jednowątkowym i nie obsługuje organizowania.

```
using namespace Windows::Foundation::Metadata;
using namespace Platform;

[Threading(ThreadingModel::STA)]
[MarshalingBehavior(MarshalingType::None)]
public ref class MySTAClass
{
};
```

Niezamkniętej klasy musi mieć organizowanie i wątki ustawienia atrybutów, tak aby kompilator może sprawdzić, czy klasy pochodne mają taką samą wartość dla tych atrybutów. Jeśli klasa nie ma ustawienia ustawione jawnie, kompilator generuje błąd i nie można skompilować. Każda klasa, która pochodzi z niezamężnej klasy generuje błąd kompilatora w jednym z tych przypadków:

- `ThreadingModel` Atrybuty `MarshallingBehavior` i nie są zdefiniowane w klasie pochodnej.

- Wartości `ThreadingModel` i `MarshallingBehavior` atrybuty w klasie pochodnej nie są zgodne z wartościami w klasie podstawowej.

Informacje dotyczące wątków i organizowania, które są wymagane przez składnik środowiska wykonawczego systemu Windows innej firmy, są określone w informacjach o rejestracji manifestu aplikacji dla składnika. Zaleca się, aby wszystkie składniki środowiska wykonawczego systemu Windows elastyczne. Gwarantuje to, że kod klienta można wywołać składnik z dowolnego wątku w aplikacji i zwiększa wydajność tych wywołań, ponieważ są one bezpośrednie wywołania, które nie mają organizowania. Jeśli chcesz klasy w ten sposób, a następnie kod `Platform::Agile<T>` klienta nie trzeba używać do korzystania z klasy.

## <a name="see-also"></a>Zobacz też

[Threadingmodel](/uwp/api/windows.foundation.metadata.threadingmodel)<br/>
[MarshallingBehavior](/uwp/api/windows.foundation.metadata.marshalingbehaviorattribute)
