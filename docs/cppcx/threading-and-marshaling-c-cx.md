---
title: "Wątkowość i organizowanie (C + +/ CX) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 12/30/2016
ms.prod: windows-client-threshold
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- C4451
helpviewer_keywords:
- threading issues, C++/CX
- agility, C++/CX
- C++/CX, threading issues
ms.assetid: 83e9ca1d-5107-4194-ae6f-e01bd928c614
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0d62da6fafccecc8099e3f9611946d1c89a40389
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="threading-and-marshaling-ccx"></a>Wątkowość i organizowanie (C + +/ CX)
W większość przypadków wystąpienia klas środowiska wykonawczego systemu Windows, takich jak standardowymi obiektami C++ są dostępne z dowolnego wątku. Takich klas są określane jako "agile". Jednak niewielkiej liczby klas środowiska wykonawczego systemu Windows, które są dostarczane z systemem Windows są z systemem innym niż agile i muszą być przetworzone więcej takich jak obiekty COM niż standardowymi obiektami C++. Nie trzeba być ekspert COM, używać klas agile, ale należy wziąć pod uwagę model wątkowości klasy i jego zachowanie marshalingu. Ten artykuł zawiera wskazówki dotyczące rzadkich scenariuszach, w których należy używać wystąpienia klasy agile i tła.  
  
## <a name="threading-model-and-marshaling-behavior"></a>Model wątkowości i zachowanie marshalingu  
 Klasa środowiska uruchomieniowego systemu Windows może obsługiwać dostępu współbieżnych wątków na różne sposoby, wskazywany przez dwa atrybuty, które są stosowane do niej:  
  
-   `ThreadingModel` atrybut może mieć jedną z wartości — STA, MTA, lub obie, zgodnie z definicją `ThreadingModel` wyliczenia.  
  
-   `MarshallingBehavior` atrybut może mieć jedną z wartości — Agile, None lub Standard, zgodnie z definicją w `MarshallingType` wyliczenia.  
  
 `ThreadingModel` Atrybut określa, gdzie jest ładowany klasy, po uaktywnieniu: tylko w kontekście wątku (STA) interfejsu użytkownika, tylko w kontekście wątku (MTA) tło lub w kontekście wątku tworzącą obiektu (oba). `MarshallingBehavior` Wartości atrybutu odnoszą się do zachowania obiektu w różnych kontekstach wątkowości; w większości przypadków, nie trzeba poznać te wartości szczegółowo.  Klasy, które są udostępniane przez interfejs API systemu Windows, mieć około 90 procent `ThreadingModel`= zarówno i `MarshallingType`= Agile. Oznacza to, że można obsługują szczegółów niskiego poziomu wątkowości przezroczyste i wydajne.   Jeśli używasz `ref new` można utworzyć klasy "agile", można wywoływać metod w nim z z wątku głównego aplikacji lub z jednego lub więcej wątków roboczych.  Innymi słowy, można użyć zwinne klasy — niezależnie od tego, czy są dostarczane przez system Windows ani przez inną firmę — z dowolnego miejsca w kodzie. Nie trzeba zajmować się klasy model wątkowości lub zachowanie marshalingu  
  
## <a name="consuming-windows-runtime-components"></a>Wykorzystywanie składników środowiska wykonawczego systemu Windows  
 Podczas tworzenia aplikacji platformy uniwersalnej systemu Windows mogą współdziałać ze składnikami zarówno agile, jak i agile. Podczas interakcji ze składnikami agile, mogą wystąpić następujące ostrzeżenie.  
  
### <a name="compiler-warning-when-consuming-non-agile-classes-c4451"></a>Ostrzeżenie kompilatora podczas używania klas agile (C4451)  
 Z różnych powodów niektóre klasy nie może być elastyczne. Jeśli dostęp do wystąpień klas agile z wątku interfejsu użytkownika i wątku w tle, należy wykonać dodatkowe zadbać zapewnić poprawne zachowanie w czasie wykonywania. Kompilator Visual C++ wystawia ostrzeżenia wystąpienia-agile klasie czasu wykonywania w aplikacji w zakresie globalnym lub zadeklarować-agile typ elementu członkowskiego klasy w tej samej klasy ref jest oznaczony jako elastyczne.  
  
 Agile klas najprostszym radzenia sobie z są te, które mają `ThreadingModel`= zarówno i `MarshallingType`= Standard.  Możesz wprowadzić te klasy agile tylko przy użyciu `Agile<T>` Klasa pomocy.   W poniższym przykładzie przedstawiono deklaracji typu-agile obiektu `Windows::Security::Credentials::UI::CredentialPickerOptions^`i w związku z tym wystawiony ostrzeżenia kompilatora.  
  
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
  
 Oto wystawiony ostrzeżenia:  
  
> `Warning 1 warning C4451: 'Platform::Agile<T>::_object' : Usage of ref class 'Windows::Security::Credentials::UI::CredentialPickerOptions' inside this context can lead to invalid marshaling of object across contexts. Consider using 'Platform::Agile<Windows::Security::Credentials::UI::CredentialPickerOptions>' instead`  
  
 Podczas dodawania odwołania — w zakresie elementu członkowskiego lub globalne — do obiektu, który ma kierowania zachowanie "Standard", kompilator generuje ostrzeżenie zaleceniem zawijać typu w `Platform::Agile<T>`: `Consider using 'Platform::Agile<Windows::Security::Credentials::UI::CredentialPickerOptions>' instead` użycie `Agile<T>`, będzie można korzystać z tej klasy jak w innych agile klasy. Użyj `Platform::Agile<T>` w takiej sytuacji:  
  
-   Agile zmienna jest zadeklarowana w zakresie globalnym.  
  
-   Agile zmienna została zadeklarowana w zakresie klasy i istnieje ryzyko, że korzystanie z kodu może smuggle wskaźnik — to znaczy używany w innego apartamentu bez organizowanie poprawne.  
  
 Jeśli żadna z tych warunków, można oznaczyć klasa zawierająca jako elastyczne. Innymi słowy, należy bezpośrednio przechowywania obiektów agile tylko w klasach agile i przechowywania obiektów agile, za pomocą Platform::Agile\<T > w klasach elastyczne.  
  
 Poniższy przykład przedstawia użycie `Agile<T>` , dzięki czemu można bezpiecznie zignorować to ostrzeżenie.  
  
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
  
 Zwróć uwagę, że `Agile` nie można przekazać jako parametru w klasie ref lub wartości zwracanej. `Agile<T>::Get()` Metoda zwraca dojście do obiektu (^) jaki może upłynąć między interfejsu binarne aplikacji (ABI) w publicznej metody lub właściwości.  
  
 W programie Visual C++, po utworzeniu odwołania do klasy środowiska wykonawczego systemu Windows w proc, która ma zachowanie marshalingu "None", kompilator ostrzeżenie C4451, ale nie sugerują, rozważ użycie `Platform::Agile<T>`.  Kompilator nie oferuje pomocy poza to ostrzeżenie, odpowiedzialność za użycie klasy poprawnie i upewnij się, że kod wywołuje STA składniki tylko z wątku interfejsu użytkownika i MTA tylko z wątku w tle.  
  
## <a name="authoring-agile-windows-runtime-components"></a>Tworzenie agile składników środowiska wykonawczego systemu Windows  
 Podczas definiowania klasy ref w języku C + +/ CX, jest domyślnie agile — to znaczy ma `ThreadingModel`= zarówno i `MarshallingType`= Agile.  Jeśli używasz [!INCLUDE[cppwrl](../cppcx/includes/cppwrl-md.md)], można utworzyć klasy agile wynikających z `FtmBase`, który korzysta z `FreeThreadedMarshaller`.  Jeśli Tworzenie klasy, która ma `ThreadingModel`= zarówno lub `ThreadingModel`= MTA, upewnij się, że klasa jest bezpieczne wątkowo. Aby uzyskać więcej informacji, zobacz [tworzenie i korzystać z obiektów (WRL)](http://msdn.microsoft.com/en-us/d5e42216-e888-4f1f-865a-b5ccd0def73e).  
  
 Można zmodyfikować modelu wątkowości i zachowanie marshalingu klasy referencyjnej. Jednak jeśli wprowadzono zmiany, które renderują klasy z systemem innym niż agile, muszą zrozumieć wpływ, które są skojarzone z tymi zmianami.  
  
 Poniższy przykład przedstawia sposób zastosowania `MarshalingBehavior` i `ThreadingModel` atrybutów klasie czasu wykonywania w bibliotece klas środowiska wykonawczego systemu Windows. Jeśli aplikacja korzysta biblioteki DLL, a `ref new` — słowo kluczowe, aby aktywować `MySTAClass` klasy obiektu, obiekt jest aktywowana w jednowątkowym apartamencie i nie obsługuje przekazywanie.  
  
```  
using namespace Windows::Foundation::Metadata;  
using namespace Platform;  
  
[Threading(ThreadingModel::STA)]  
[MarshalingBehavior(MarshalingType::None)]   
public ref class MySTAClass  
{  
};  
  
```  
 
 Niezapieczętowany klasy musi mieć ustawienia atrybutu organizowania i wątków, tak aby kompilator można sprawdzić, czy klas pochodnych mają taką samą wartość dla tych atrybutów. Jeśli klasa nie ma ustawienia ustawiony w sposób jawny, kompilator generuje błąd i kompilacji. Wszystkie klasy, która jest pochodną unsealedclass generuje błąd kompilatora w tych przypadkach:  
  
-   `ThreadingModel` i `MarshallingBehavior` atrybuty nie są zdefiniowane w klasie pochodnej.  
  
-   Wartości `ThreadingModel` i `MarshallingBehavior` atrybutów w klasie pochodnej nie odpowiadają wartościom w klasie podstawowej.  
  
 W aplikacji informacje rejestracyjne manifestu składnika określono wątków i przekazywanie informacji wymaganych przez składnik środowiska wykonawczego systemu Windows innych firm. Zaleca się wykonanie wszystkich składników środowiska wykonawczego systemu Windows elastyczne. Dzięki temu można wywołać składnika z dowolnego wątku w aplikacji kod klienta i poprawia wydajność wywołań, ponieważ są one bezpośrednie wywołania, które mają nie przekazywanie. Tworzenie klasy w ten sposób, a następnie kod klienta nie trzeba używać `Platform::Agile<T>` użycie klasy.  
  
## <a name="see-also"></a>Zobacz też  
 [ThreadingModel](http://msdn.microsoft.com/library/windows/apps/xaml/windows.foundation.metadata.threadingmodel.aspx)   
 [MarshallingBehavior](http://msdn.microsoft.com/library/windows/apps/xaml/windows.foundation.metadata.marshalingbehaviorattribute.aspx)