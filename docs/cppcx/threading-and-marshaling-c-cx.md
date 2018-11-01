---
title: Wątkowość i Marshaling (C + +/ CX)
ms.date: 12/30/2016
f1_keywords:
- C4451
helpviewer_keywords:
- threading issues, C++/CX
- agility, C++/CX
- C++/CX, threading issues
ms.assetid: 83e9ca1d-5107-4194-ae6f-e01bd928c614
ms.openlocfilehash: faf541a0705de3e0e3d1b795d1abbdc2e9707974
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50582640"
---
# <a name="threading-and-marshaling-ccx"></a>Wątkowość i Marshaling (C + +/ CX)

W zdecydowanej większości przypadków wystąpienia klas środowiska wykonawczego Windows, takich jak standardowymi obiektami C++ jest możliwy z żadnym z wątków. Takich klas są określane jako "agile". Jednak niewielkiej liczby klasy środowiska wykonawczego Windows, które są dostarczane z Windows są inne niż agile i należy wykorzystać w bardziej podobnie jak obiekty COM niż standardowymi obiektami C++. Nie musisz być ekspertem COM, używać klas agile, ale należy wziąć pod uwagę klasy modelu wątkowości i jego zachowanie organizowania. Ten artykuł zawiera wskazówki dotyczące tych rzadkich scenariuszach, w których należy używać wystąpienia klasy — agile i tła.

## <a name="threading-model-and-marshaling-behavior"></a>Model wątkowości i zachowanie marshalingu

Klasy środowiska wykonawczego Windows może obsługiwać dostępu współbieżnych wątków na różne sposoby, wskazane przez dwa atrybuty, które są stosowane do niego:

- `ThreadingModel` atrybut może mieć jedną z wartości — STA, MTA, lub oba, zgodnie z definicją `ThreadingModel` wyliczenia.

- `MarshallingBehavior` atrybut może mieć jedną z wartości — metodyki Agile, None, lub Standard, zgodnie z definicją `MarshallingType` wyliczenia.

`ThreadingModel` Atrybut określa, gdzie jest ładowany klasy, po aktywowaniu: wyłącznie w kontekście wątku (STA) interfejsu użytkownika, tylko w kontekście wątku (MTA) tło lub w kontekście wątku, który tworzy obiekt (oba). `MarshallingBehavior` Wartości atrybutu odnoszą się do zachowania obiektu w różnych kontekstach wątków; w większości przypadków nie musisz zrozumieć te wartości szczegółowo.  Klas, które są dostarczane przez interfejs API Windows, ma około 90 procent `ThreadingModel`= zarówno i `MarshallingType`= Agile. Oznacza to, czy szczegóły niskiego poziomu wątków może obsługują przezroczyste i wydajne.   Kiedy używasz `ref new` Aby utworzyć klasę "agile", można wywoływać metody na nim z wątku usługi głównej aplikacji lub z jednego lub więcej wątków roboczych.  Innymi słowy, można użyć klasy agile — niezależnie od tego, czy podane przez Windows lub innej — z dowolnego miejsca w kodzie. Nie trzeba zajmować się klasy model wątkowości lub zachowanie marshalingu

## <a name="consuming-windows-runtime-components"></a>Wykorzystywanie składników środowiska wykonawczego Windows

Podczas tworzenia aplikacji uniwersalnych platformy Windows, możesz wchodzić w interakcje składniki agile i agile. Podczas interakcji ze składnikami agile, mogą wystąpić następujące ostrzeżenie.

### <a name="compiler-warning-c4451-when-consuming-non-agile-classes"></a>Kompilator ostrzeżenie C4451 podczas używania klas agile

Z różnych powodów niektóre klasy nie może być agile. Jeśli uzyskujesz dostęp do wystąpienia klas agile z wątku interfejsu użytkownika i wątku w tle, należy wykonać dodatkowe istotne do zapewnienia poprawnego zachowania w czasie wykonywania. Kompilator języka Visual C++ generuje ostrzeżenia podczas tworzenia wystąpienia-agile klasy środowiska wykonawczego w aplikacji w zakresie globalnym lub deklaracja typu agile, jako element członkowski klasy w klasie ref, który sam jest oznaczony jako agile.

Agile klas najprostszym radzenia sobie z są te, które mają `ThreadingModel`= zarówno i `MarshallingType`= Standard.  Aby włączyć te klasy agile tylko za pomocą `Agile<T>` Klasa pomocy.   W poniższym przykładzie pokazano deklarację-agile obiektu typu `Windows::Security::Credentials::UI::CredentialPickerOptions^`i ostrzeżenia kompilatora, w wyniku wystawiony.

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

Ostrzeżenie, wystawiany jest następujący:

> `Warning 1 warning C4451: 'Platform::Agile<T>::_object' : Usage of ref class 'Windows::Security::Credentials::UI::CredentialPickerOptions' inside this context can lead to invalid marshaling of object across contexts. Consider using 'Platform::Agile<Windows::Security::Credentials::UI::CredentialPickerOptions>' instead`

Po dodaniu odwołania — w zakresie elementu członkowskiego lub zakresu globalnego — do obiektu, który ma zachowanie marshalingu "Standardowa", kompilator generuje ostrzeżenie z informacją o tym, aby opakować typ w `Platform::Agile<T>`: `Consider using 'Platform::Agile<Windows::Security::Credentials::UI::CredentialPickerOptions>' instead` Jeśli używasz `Agile<T>`, będzie można korzystać z klasy jak w przypadku dowolnej klasy agile. Użyj `Platform::Agile<T>` w takiej sytuacji:

- Agile zmienna jest zadeklarowana w zakresie globalnym.

- Agile zmienna jest zadeklarowana w zakresie klasy i istnieje ryzyko, że korzystanie z kodu może być smuggle wskaźnik — oznacza to, korzystać z niego w różnych apartamentu bez marshaling poprawne.

Jeśli żadna z tych warunków zastosowania, można oznaczyć klasa zawierająca jako agile. Innymi słowy, należy bezpośrednio przechowywania obiektów agile tylko w klasach agile i przechowywania obiektów agile, za pośrednictwem Platform::Agile\<T > w klasach agile.

Poniższy przykład pokazuje, jak używać `Agile<T>` , dzięki czemu można bezpiecznie zignorować to ostrzeżenie.

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

Należy zauważyć, że `Agile` nie mogą być przekazywane jako wartość zwracana lub parametr w klasie ref. `Agile<T>::Get()` Metoda zwraca dojście do obiektu (^), którą można przekazać między interfejsem binarnym aplikacji (ABI) w publiczną metodę lub właściwość.

W programie Visual C++, po utworzeniu odwołania do klasy środowiska wykonawczego Windows w proc, która ma zachowanie marshalingu "None", kompilator generuje ostrzeżenie C4451, ale nie sugerują, rozważ użycie `Platform::Agile<T>`.  Kompilator nie oferuje pomocy poza tym ostrzeżeniu, dlatego jest odpowiedzialny za korzystanie z klasy poprawnie i upewnij się, że Twój kod wywołuje składniki STA, tylko z wątku interfejsu użytkownika i składniki MTA tylko z wątku w tle.

## <a name="authoring-agile-windows-runtime-components"></a>Tworzenie agile składników środowiska wykonawczego Windows

Podczas definiowania klasy referencyjnej w języku C + +/ CX jest agile domyślnie — oznacza to, że ma ona `ThreadingModel`= zarówno i `MarshallingType`= Agile.  Jeśli używasz Biblioteka szablonów C++ środowiska wykonawczego Windows, możesz wprowadzić klasy agile, wynikające z `FtmBase`, który używa `FreeThreadedMarshaller`.  Jeśli tworzysz klasę, która ma `ThreadingModel`= zarówno lub `ThreadingModel`= MTA, upewnij się, że klasa jest metodą o bezpiecznych wątkach.

Można zmodyfikować model wątkowości i zachowanie marshalingu klasy referencyjnej. Jednak jeśli wprowadzisz zmiany, które renderują klasy bez agile, musisz rozumieć konsekwencje, które są skojarzone z tymi zmianami.

Poniższy przykład pokazuje, jak zastosować `MarshalingBehavior` i `ThreadingModel` atrybutów do klasy środowiska uruchomieniowego w bibliotece klas środowiska wykonawczego Windows. Jeśli aplikacja korzysta z biblioteki DLL i korzysta z `ref new` — słowo kluczowe, aby aktywować `MySTAClass` klasy obiektu, jest ono aktywowane w jednowątkowym apartamentem i nie obsługuje kierowanie obiektu.

```
using namespace Windows::Foundation::Metadata;
using namespace Platform;

[Threading(ThreadingModel::STA)]
[MarshalingBehavior(MarshalingType::None)]
public ref class MySTAClass
{
};
```

Niezapieczętowane klasy musi mieć ustawienia atrybut organizowania i wątków, tak, aby kompilator może sprawdzić, czy pochodne mają taką samą wartość dla tych atrybutów. Jeśli klasa nie ma ustawienia ustawiony w sposób jawny, kompilator generuje błąd i nie zostanie skompilowany. Każda klasa, która jest pochodną unsealedclass generuje błąd kompilatora w jednym z następujących przypadkach:

- `ThreadingModel` i `MarshallingBehavior` atrybuty nie są zdefiniowane w klasie pochodnej.

- Wartości `ThreadingModel` i `MarshallingBehavior` atrybutów w klasie pochodnej nie odpowiadają wartościom w klasie bazowej.

Wątkowość i marshaling informacje wymagane przez składnik środowiska uruchomieniowego Windows innej firmy jest określona w aplikacji informacje rejestracyjne manifestu składnika. Firma Microsoft zaleca wykonanie wszystkie składniki środowiska wykonawczego Windows agile. Dzięki temu kod klienta może wywołać składnika z żadnym z wątków w aplikacji i poprawia wydajność te wywołania, ponieważ są one bezpośrednie wywołania, które mają nie marshaling. Jeśli Tworzenie klasy w ten sposób, a następnie kod klienta, nie trzeba używać `Platform::Agile<T>` korzystanie z klasy.

## <a name="see-also"></a>Zobacz też

[ThreadingModel](https://msdn.microsoft.com/library/windows/apps/xaml/windows.foundation.metadata.threadingmodel.aspx)<br/>
[MarshallingBehavior](https://msdn.microsoft.com/library/windows/apps/xaml/windows.foundation.metadata.marshalingbehaviorattribute.aspx)