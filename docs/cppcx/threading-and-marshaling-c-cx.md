---
title: Wątkowość i kierowanie (C++/CX)
ms.date: 12/30/2016
f1_keywords:
- C4451
helpviewer_keywords:
- threading issues, C++/CX
- agility, C++/CX
- C++/CX, threading issues
ms.assetid: 83e9ca1d-5107-4194-ae6f-e01bd928c614
ms.openlocfilehash: 05601367b6907e34d9d67364d35988a37ceae40c
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70741128"
---
# <a name="threading-and-marshaling-ccx"></a>Wątkowość i kierowanie (C++/CX)

W większości przypadków wystąpienia klas środowisko wykonawcze systemu Windows, takich jak obiekty standardowe C++ , są dostępne z dowolnego wątku. Takie klasy są określane jako "Agile". Jednak niewielka liczba klas środowisko wykonawcze systemu Windows, które są dostarczane z systemem Windows, nie są Agile i muszą być używane podobnie jak obiekty COM niż obiekty C++ standardowe. Nie musisz być ekspertem COM, aby używać klas innych niż Agile, ale musisz wziąć pod uwagę model wątkowości klasy i jego zachowanie organizacyjne. Ten artykuł zawiera ogólne i wskazówki dotyczące tych rzadkich scenariuszy, w których należy użyć wystąpienia klasy nieagile.

## <a name="threading-model-and-marshaling-behavior"></a>Model wątkowości i zachowanie organizowania

Klasa środowisko wykonawcze systemu Windows może obsługiwać współbieżny dostęp do wątków na różne sposoby, zgodnie z wyznaczonymi przez dwa atrybuty, które są do niego stosowane:

- `ThreadingModel`atrybut może mieć jedną z wartości — sta, MTA lub oba, zgodnie z `ThreadingModel` definicją w wyliczeniu.

- `MarshallingBehavior`atrybut może mieć jedną z wartości — Agile, None lub standard zgodnie z `MarshallingType` definicją w wyliczeniu.

`ThreadingModel` Atrybut określa, gdzie Klasa jest ładowana po aktywowaniu: tylko w kontekście wątek interfejsu użytkownika (STA), tylko w kontekście wątku w tle (MTA) lub w kontekście wątku, który tworzy obiekt (oba). Wartości `MarshallingBehavior` atrybutów odnoszą się do zachowania obiektu w różnych kontekstach wątków. w większości przypadków nie trzeba zrozumieć tych wartości szczegółowo.  Klas dostarczanych przez interfejs API systemu Windows o 90% ma `ThreadingModel`= oba i `MarshallingType`= Agile. Oznacza to, że mogą one obsługiwać informacje o wątkach niskiego poziomu w sposób przezroczysty i wydajny.   W przypadku użycia `ref new` do tworzenia klasy "Agile" można wywołać metody z głównego wątku aplikacji lub z jednego lub większej liczby wątków roboczych.  Innymi słowy, można użyć klasy Agile — niezależnie od tego, czy jest ona udostępniana przez system Windows, czy przez inną firmę — od dowolnego miejsca w kodzie. Nie musisz być zaangażowane w model wątkowości klasy ani zachowanie organizowania.

## <a name="consuming-windows-runtime-components"></a>Zużywanie składników środowisko wykonawcze systemu Windows

Podczas tworzenia aplikacji platforma uniwersalna systemu Windows można korzystać z elementów Agile i innych niż Agile. W przypadku korzystania z składników innych niż Agile może wystąpić poniższe ostrzeżenie.

### <a name="compiler-warning-c4451-when-consuming-non-agile-classes"></a>Ostrzeżenie kompilatora C4451 podczas konsumowania klas nieagile

Z różnych powodów niektóre klasy nie mogą być elastyczne. Jeśli uzyskujesz dostęp do wystąpień klas innych niż Agile z wątku interfejsu użytkownika i wątku w tle, weź pod uwagę dodatkowe zachowanie w czasie wykonywania. Kompilator firmy C++ Microsoft wystawia ostrzeżenia podczas tworzenia wystąpienia klasy czasu wykonywania nieagile w aplikacji w zakresie globalnym lub deklarowania typu nieagile jako składowej klasy w klasie referencyjnej, która jest oznaczona jako Agile.

W przypadku klas innych niż Agile najłatwiej jest zająć się tymi, które mają `ThreadingModel`= oba i `MarshallingType`= Standard.  Te klasy można przyagile tylko przy użyciu `Agile<T>` klasy pomocnika.   Poniższy przykład przedstawia deklarację nieagile obiektu typu `Windows::Security::Credentials::UI::CredentialPickerOptions^`oraz Ostrzeżenie kompilatora, który został wystawiony w wyniku.

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

Oto ostrzeżenie, które zostało wystawione:

> `Warning 1 warning C4451: 'Platform::Agile<T>::_object' : Usage of ref class 'Windows::Security::Credentials::UI::CredentialPickerOptions' inside this context can lead to invalid marshaling of object across contexts. Consider using 'Platform::Agile<Windows::Security::Credentials::UI::CredentialPickerOptions>' instead`

Po dodaniu odwołania — w zakresie elementu członkowskiego lub zakresu globalnego — do obiektu, który ma zachowanie kierujące "Standardowa", kompilator generuje ostrzeżenie, które doradza, aby zawinąć typ w `Platform::Agile<T>`: `Consider using 'Platform::Agile<Windows::Security::Credentials::UI::CredentialPickerOptions>' instead`Jeśli używasz, `Agile<T>`możesz użyć klasy, takiej jak każda inna Klasa Agile. `Platform::Agile<T>` W następujących okolicznościach:

- Zmienna nieagile jest zadeklarowana w zakresie globalnym.

- Zmienna inna niż Agile jest zadeklarowana w zakresie klasy i istnieje szansa, że zużywający kod może przemytić wskaźnik, czyli używać go w innej lokalizacji bez poprawnego organizowania.

Jeśli żaden z tych warunków nie zostanie spełniony, można oznaczyć zawierającą klasę jako nieagile. Innymi słowy, należy bezpośrednio przechowywać obiekty nieagile tylko w klasach nieagile i przechowywać obiekty nieagile za pośrednictwem platformy:: Agile\<T > w klasach Agile.

Poniższy przykład pokazuje, jak użyć `Agile<T>` , aby można było bezpiecznie zignorować to ostrzeżenie.

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

Należy zauważyć `Agile` , że nie można przesłać jako wartości zwracanej lub parametru w klasie referencyjnej. `Agile<T>::Get()` Metoda zwraca dojście do obiektu (^), które można przekazać przez interfejs binarny aplikacji (ABI) do publicznej metody lub właściwości.

Gdy tworzysz odwołanie do klasy środowisko wykonawcze systemu Windows w proc, która ma zachowanie Marshaling "none", kompilator wystawia ostrzeżenie C4451, ale nie sugeruje, że należy rozważyć użycie `Platform::Agile<T>`.  Kompilator nie może zaoferować żadnej pomocy poza tym ostrzeżeniem, dlatego jest odpowiedzialny za korzystanie z klasy prawidłowo i upewnij się, że kod wywołuje składniki STA tylko z wątku interfejsu użytkownika i składnika MTA tylko z wątku w tle.

## <a name="authoring-agile-windows-runtime-components"></a>Tworzenie składników środowisko wykonawcze systemu Windows Agile

Gdy definiujesz klasę ref w C++/CX, jest ona domyślnie Agile — to znaczy, że ma `ThreadingModel`= oba i `MarshallingType`= Agile.  Jeśli używasz biblioteki szablonów środowisko wykonawcze systemu Windows C++ , możesz zmienić klasę, wyprowadzając ją z `FtmBase` `FreeThreadedMarshaller`, która używa.  Jeśli tworzysz klasę, która ma `ThreadingModel`= Both lub `ThreadingModel`= MTA, upewnij się, że Klasa jest bezpieczna wątkowo.

Można zmodyfikować model wątkowości i zachowanie związane z kierowaniem klasy referencyjnej. Jeśli jednak wprowadzisz zmiany, które renderują klasę nieagile, musisz zrozumieć konsekwencje związane z tymi zmianami.

Poniższy przykład pokazuje, jak zastosować `MarshalingBehavior` i `ThreadingModel` atrybuty do klasy środowiska uruchomieniowego w bibliotece klas środowisko wykonawcze systemu Windows. Gdy aplikacja używa biblioteki DLL i używa `ref new` słowa kluczowego do `MySTAClass` uaktywnienia obiektu klasy, obiekt jest aktywowany w jednowątkowym apartamentie i nie obsługuje organizowania.

```
using namespace Windows::Foundation::Metadata;
using namespace Platform;

[Threading(ThreadingModel::STA)]
[MarshalingBehavior(MarshalingType::None)]
public ref class MySTAClass
{
};
```

Niezapieczętowane klasy muszą mieć ustawienia atrybutu organizowania i wątkowości, aby kompilator mógł sprawdzić, czy klasy pochodne mają tę samą wartość dla tych atrybutów. Jeśli Klasa nie ma ustawionych ustawień jawnie, kompilator generuje błąd i kompilacja nie powiedzie się. Każda klasa, która pochodzi od unsealedclass, generuje błąd kompilatora w jednym z następujących przypadków:

- Atrybuty `ThreadingModel` i`MarshallingBehavior` nie są zdefiniowane w klasie pochodnej.

- Wartości atrybutów `ThreadingModel` i `MarshallingBehavior` w klasie pochodnej nie są zgodne z wartościami w klasie bazowej.

Informacje o wątkach i kierowaniu wymagane przez składnik środowisko wykonawcze systemu Windows innej firmy są określone w informacjach o rejestracji manifestu aplikacji dla składnika. Zalecamy, aby wszystkie składniki środowisko wykonawcze systemu Windows były Agile. Dzięki temu kod klienta może wywoływać składnik z dowolnego wątku w aplikacji, a także zwiększyć wydajność tych wywołań, ponieważ są to bezpośrednie wywołania, które nie mają organizowania. Jeśli utworzysz swoją klasę w ten sposób, kod klienta nie musi używać do korzystania `Platform::Agile<T>` z klasy.

## <a name="see-also"></a>Zobacz także

[ThreadingModel](/uwp/api/Windows.Foundation.Metadata.ThreadingModel)<br/>
[MarshallingBehavior](/uwp/api/windows.foundation.metadata.marshalingbehaviorattribute)
