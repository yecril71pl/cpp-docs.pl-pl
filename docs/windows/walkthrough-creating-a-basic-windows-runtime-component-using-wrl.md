---
title: "Wskazówki: Tworzenie składnika środowiska uruchomieniowego podstawowa systemu Windows za pomocą biblioteki WRL | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: C++
ms.assetid: 6e3f0986-7905-4f94-90e5-22c2ebfc8cd0
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5859f3ebfcb55427e239a0018d539e2f4df13800
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="walkthrough-creating-a-basic-windows-runtime-component-using-wrl"></a>Wskazówki: tworzenie podstawowego składnika środowiska wykonawczego systemu Windows za pomocą biblioteki WRL
Ten dokument przedstawia sposób Windows środowiska uruchomieniowego C++ szablonu biblioteki (WRL) umożliwia tworzenie podstawowego składnika środowiska wykonawczego systemu Windows. Składnik dodaje dwie liczby i zgłasza zdarzenie, gdy wynik jest pierwsze. Ten dokument przedstawiono również sposób użycia składnika z aplikacji platformy uniwersalnej systemu Windows, który używa języka JavaScript.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
  
-   Obsługa przy użyciu z [środowiska wykonawczego systemu Windows](http://msdn.microsoft.com/library/windows/apps/br211377.aspx).  
  
-   Środowisko z modelu COM.  
  
### <a name="to-create-a-basic-windows-runtime-component-that-adds-two-numbers"></a>Aby utworzyć podstawowego składnika środowiska wykonawczego systemu Windows, która dodaje dwie liczby  
  
1.  W programie Visual Studio Utwórz Visual C++ `WRLClassLibrary` projektu. Dokument [szablon projektu biblioteki klas](../windows/wrl-class-library-project-template.md) zawiera opis sposobu pobierania tego szablonu. Nazwij projekt `Contoso`.  
  
2.  W Contoso.cpp i Contoso.idl należy zastąpić wszystkie wystąpienia elementu "WinRTClass" z "Kalkulatora".  
  
3.  W Contoso.idl, Dodaj `Add` metodę `ICalculator` interfejsu.  
  
     [!code-cpp[wrl-basic-component#1](../windows/codesnippet/CPP/walkthrough-creating-a-basic-windows-runtime-component-using-wrl_1.idl)]  
  
4.  W Contoso.cpp, Dodaj `Add` metodę `public` sekcji `Calculator` klasy.  
  
     [!code-cpp[wrl-basic-component#2](../windows/codesnippet/CPP/walkthrough-creating-a-basic-windows-runtime-component-using-wrl_2.cpp)]  
  
    > [!IMPORTANT]
    >  Ponieważ tworzysz składnika modelu COM, należy użyć `__stdcall` konwencji wywoływania.  
  
     Firma Microsoft zaleca użycie `_Out_` i innych adnotacji źródła adnotacji języka (SAL) do opisywania, jak funkcja korzysta z jego parametrów. Adnotacje SAL opisano również wartości zwracanych. Adnotacje SAL pracować z [narzędzia do analizy kodu C/C++](/visualstudio/code-quality/code-analysis-for-c-cpp-overview) aby wykryć możliwe wady C i C++ kod źródłowy. Przepełnienia buforów, niezainicjowanej pamięci obejmują typowe błędy kodowania, które są zgłaszane przez narzędzie, wyłuskań wskaźnika o wartości null i przecieków pamięci i zasobów.  
  
### <a name="to-use-the-component-from-a-universal-windows-platform-app-that-uses-javascript"></a>Aby użyć składnika z aplikacji platformy uniwersalnej systemu Windows, który używa języka JavaScript  
  
1.  W programie Visual Studio, Dodaj nowe JavaScript `Blank App` projektu do `Contoso` rozwiązania. Nazwij projekt `CalculatorJS`.  
  
2.  W `CalculatorJS` projekt, Dodaj odwołanie do `Contoso` projektu.  
  
3.  W default.html, Zastąp `body` sekcji z tych elementów interfejsu użytkownika:  
  
     [!code-html[wrl-basic-component#3](../windows/codesnippet/Html/walkthrough-creating-a-basic-windows-runtime-component-using-wrl_3.html)]  
  
4.  W default.js, należy zaimplementować `OnClick` funkcji.  
  
     [!code-javascript[wrl-basic-component#4](../windows/codesnippet/JavaScript/walkthrough-creating-a-basic-windows-runtime-component-using-wrl_4.js)]  
  
    > [!NOTE]
    >  W języku JavaScript pierwsza litera Nazwa metody jest zmieniany na małe litery, aby dopasować standardowej konwencji nazewnictwa.  
  
### <a name="to-add-an-event-that-fires-when-a-prime-number-is-calculated"></a>Aby dodać zdarzenie, które są generowane, gdy liczba pierwsza jest obliczana  
  
1.  W Contoso.idl przed deklaracja `ICalculator`, typ delegata `PrimeNumberEvent`, co umożliwia `int` argumentu.  
  
     [!code-cpp[wrl-basic-component#5](../windows/codesnippet/CPP/walkthrough-creating-a-basic-windows-runtime-component-using-wrl_5.idl)]  
  
     Jeśli używasz `delegate` — słowo kluczowe, kompilator MIDL tworzy interfejs, który zawiera `Invoke` metodę, która odpowiada podpisu tego delegata. W tym przykładzie wygenerowanego pliku Contoso_h.h definiuje `IPrimeNumberEvent` interfejs, który jest używany w dalszej części tej procedury.  
  
     [!code-cpp[wrl-basic-component#13](../windows/codesnippet/CPP/walkthrough-creating-a-basic-windows-runtime-component-using-wrl_6.cpp)]  
  
2.  W `ICalculator` interfejsu, zdefiniuj `PrimeNumberFound` zdarzeń. `eventadd` i `eventremove` atrybuty określić, że klient `ICalculator` interfejs może subskrybować i subskrypcję tego zdarzenia.  
  
     [!code-cpp[wrl-basic-component#6](../windows/codesnippet/CPP/walkthrough-creating-a-basic-windows-runtime-component-using-wrl_7.idl)]  
  
3.  W Contoso.cpp, Dodaj `private` [Microsoft::WRL::EventSource](../windows/eventsource-class.md) zmiennej członka do zarządzania subskrybentów zdarzeń i wywołania programu obsługi zdarzeń.  
  
     [!code-cpp[wrl-basic-component#7](../windows/codesnippet/CPP/walkthrough-creating-a-basic-windows-runtime-component-using-wrl_8.cpp)]  
  
4.  W Contoso.cpp, należy zaimplementować `add_PrimeNumberFound` i `remove_PrimeNumberFound` metody.  
  
     [!code-cpp[wrl-basic-component#8](../windows/codesnippet/CPP/walkthrough-creating-a-basic-windows-runtime-component-using-wrl_9.cpp)]  
  
### <a name="to-raise-the-event-when-a-prime-number-is-calculated"></a>Aby zgłosić zdarzenie, gdy liczba pierwsza jest obliczana  
  
1.  W Contoso.cpp, Dodaj `IsPrime` metodę `private` sekcji `Calculator` klasy.  
  
     [!code-cpp[wrl-basic-component#12](../windows/codesnippet/CPP/walkthrough-creating-a-basic-windows-runtime-component-using-wrl_10.cpp)]  
  
2.  Modyfikowanie `Calculator`w `Add` metodę do wywołania [Microsoft::WRL::EventSource::InvokeAll](../windows/eventsource-invokeall-method.md) metoda obliczania liczba pierwsza.  
  
     [!code-cpp[wrl-basic-component#11](../windows/codesnippet/CPP/walkthrough-creating-a-basic-windows-runtime-component-using-wrl_11.cpp)]  
  
### <a name="to-handle-the-event-from-javascript"></a>Obsługa zdarzenia z kodu JavaScript  
  
1.  Default.html, zmodyfikuj `body` sekcji, aby uwzględnić obszaru tekstu, który zawiera liczb pierwszych.  
  
     [!code-html[wrl-basic-component#9](../windows/codesnippet/Html/walkthrough-creating-a-basic-windows-runtime-component-using-wrl_12.html)]  
  
2.  Default.js, zmodyfikuj `Add` funkcji obsługi `PrimeNumberFound` zdarzeń. Program obsługi zdarzeń dołącza liczba pierwsza do obszaru tekstu, która została zdefiniowana w poprzednim kroku.  
  
     [!code-javascript[wrl-basic-component#10](../windows/codesnippet/JavaScript/walkthrough-creating-a-basic-windows-runtime-component-using-wrl_13.js)]  
  
    > [!NOTE]
    >  W języku JavaScript nazwy zdarzenia nie zostaną zmienione na małe i jest dołączany na początku z "on" odpowiadające standardowej konwencji nazewnictwa.  
  
 Na poniższej ilustracji przedstawiono podstawowe aplikacji Kalkulator.  
  
 ![Kalkulator podstawowe aplikacji przy użyciu języka JavaScript](../windows/media/wrl_basic_component.png "WRL_Basic_Component")  
  
## <a name="next-steps"></a>Następne kroki  
  
## <a name="see-also"></a>Zobacz też  
 [Biblioteka szablonów C++ środowiska wykonawczego systemu Windows (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md)   
 [Szablon projektu biblioteki klas](../windows/wrl-class-library-project-template.md)   
 [Narzędzie do analizy kodu C/C++](/visualstudio/code-quality/code-analysis-for-c-cpp-overview)