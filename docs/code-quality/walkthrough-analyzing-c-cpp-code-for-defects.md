---
title: 'Przewodnik: Analizowanie kodu C/C++ dla wad'
description: Pokazuje, jak używać analizy kodu w programie Microsoft C++ w programie Visual Studio.
ms.date: 04/14/2020
ms.topic: conceptual
helpviewer_keywords:
- C/C++, code analysis
- code analysis, walkthroughs
- code, analyzing C/C++
- code analysis tool, walkthroughs
ms.openlocfilehash: 65da18f5f6d1972276f1cb8e306e82314282e40a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227715"
---
# <a name="walkthrough-analyzing-cc-code-for-defects"></a>Przewodnik: Analizowanie kodu C/C++ dla wad

W tym instruktażu pokazano, jak analizować kod C/C++ pod kątem potencjalnych usterek kodu. Używa narzędzi do analizy kodu dla kodu C/C++.

W tym instruktażu przedstawiono następujące instrukcje:

- Uruchom analizę kodu w kodzie natywnym.
- Analizuj ostrzeżenia wady kodu.
- Traktuj ostrzeżenie jako błąd.
- Adnotuj kod źródłowy, aby poprawić analizę wad kodu.

## <a name="prerequisites"></a>Wymagania wstępne

- Kopia [przykładu CppDemo](../code-quality/demo-sample.md).
- Podstawowe informacje o języku C/C++.

## <a name="run-code-analysis-on-native-code"></a>Uruchom analizę kodu w kodzie natywnym

### <a name="to-run-code-defect-analysis-on-native-code"></a>Aby uruchomić analizę wad kodu w kodzie natywnym

::: moniker range=">=vs-2019"

1. Otwórz rozwiązanie CppDemo w programie Visual Studio.

     Rozwiązanie CppDemo teraz wypełnia **Eksplorator rozwiązań**.

1. W menu **kompilacja** wybierz polecenie **Kompiluj ponownie rozwiązanie**.

     Rozwiązanie kompiluje się bez błędów lub ostrzeżeń.

1. W **Eksplorator rozwiązań**wybierz projekt CodeDefects.

1. W menu **projekt** wybierz polecenie **Właściwości**.

     Zostanie wyświetlone okno dialogowe **strony właściwości CodeDefects** .

1. Wybierz stronę właściwości **Analiza kodu** .

1. Zmień właściwość **Włącz analizę kodu na kompilacja** na **tak**. Wybierz **przycisk OK** , aby zapisać zmiany.

1. Skompiluj ponownie projekt CodeDefects.

     Ostrzeżenia analizy kodu są wyświetlane w oknie **Lista błędów** .

::: moniker-end

::: moniker range="<=vs-2017"

1. Otwórz rozwiązanie CppDemo w programie Visual Studio.

     Rozwiązanie CppDemo teraz wypełnia **Eksplorator rozwiązań**.

1. W menu **kompilacja** wybierz polecenie **Kompiluj ponownie rozwiązanie**.

     Rozwiązanie kompiluje się bez błędów lub ostrzeżeń.

     > [!NOTE]
     > W programie Visual Studio 2017 w aparacie IntelliSense może zostać wyświetlone ostrzeżenie fałszywe `E1097 unknown attribute "no_init_all"` . Możesz bezpiecznie zignorować to ostrzeżenie.

1. W **Eksplorator rozwiązań**wybierz projekt CodeDefects.

1. W menu **projekt** wybierz polecenie **Właściwości**.

     Zostanie wyświetlone okno dialogowe **strony właściwości CodeDefects** .

1. Wybierz stronę właściwości **Analiza kodu** .

1. Zaznacz pole wyboru **Włącz analizę kodu podczas kompilacji** . Wybierz **przycisk OK** , aby zapisać zmiany.

1. Skompiluj ponownie projekt CodeDefects.

     Ostrzeżenia analizy kodu są wyświetlane w oknie **Lista błędów** .

::: moniker-end

### <a name="to-analyze-code-defect-warnings"></a>Aby analizować ostrzeżenia defektu kodu

1. W menu **Widok** wybierz **Lista błędów**.

     Ten element menu może być niewidoczny. Jest to zależne od profilu dewelopera wybranego w programie Visual Studio. Być może trzeba będzie wskazać **inne okna** w menu **Widok** , a następnie wybrać **Lista błędów**.

1. W oknie **Lista błędów** kliknij dwukrotnie następujące ostrzeżenie:

     C6230: niejawne rzutowanie między różnymi semantycznie typami: użycie HRESULT w kontekście Boolean.

     W edytorze kodu jest wyświetlany wiersz, który spowodował ostrzeżenie wewnątrz funkcji `bool ProcessDomain()` . To ostrzeżenie wskazuje, że `HRESULT` jest używana w instrukcji "If", gdzie oczekiwano wyniku logicznego. Zwykle jest to błąd, ponieważ kiedy `S_OK` wynik HRESULT jest zwracany z funkcji, wskazuje na powodzenie, ale po przekonwertowaniu na wartość logiczną, która jest szacowana **`false`** .

1. Popraw to ostrzeżenie przy użyciu `SUCCEEDED` makra, które jest konwertowane na, **`true`** gdy `HRESULT` wartość zwracana wskazuje na powodzenie. Kod powinien wyglądać podobnie do następującego kodu:

   ```cpp
   if (SUCCEEDED(ReadUserAccount()))
   ```

1. W **Lista błędów**kliknij dwukrotnie następujące ostrzeżenie:

     C6282: nieprawidłowy operator: przypisanie stałej w kontekście Boolean. Rozważ użycie zamiast tego "= =".

1. Popraw to ostrzeżenie, sprawdzając pod kątem równości. Kod powinien wyglądać podobnie do następującego kodu:

   ```cpp
   if ((len == ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != L'\\'))
   ```

1. Popraw pozostałe ostrzeżenia C6001 w **Lista błędów** przez zainicjowanie `i` i `j` do 0.

1. Skompiluj ponownie projekt CodeDefects.

     Projekt kompiluje się bez żadnych ostrzeżeń lub błędów.

## <a name="correct-source-code-annotation-warnings"></a>Popraw ostrzeżenia dotyczące adnotacji kodu źródłowego

### <a name="to-enable-the-source-code-annotation-warnings-in-annotationc"></a>Aby włączyć ostrzeżenia adnotacji kodu źródłowego w adnotacji. c

::: moniker range=">=vs-2019"

1. W Eksplorator rozwiązań wybierz projekt adnotacji.

1. W menu **projekt** wybierz polecenie **Właściwości**.

     Zostanie wyświetlone okno dialogowe **strony właściwości adnotacji** .

1. Wybierz stronę właściwości **Analiza kodu** .

1. Zmień właściwość **Włącz analizę kodu na kompilacja** na **tak**. Wybierz **przycisk OK** , aby zapisać zmiany.

::: moniker-end

::: moniker range="<=vs-2017"

1. W Eksplorator rozwiązań wybierz projekt adnotacji.

1. W menu **projekt** wybierz polecenie **Właściwości**.

     Zostanie wyświetlone okno dialogowe **strony właściwości adnotacji** .

1. Wybierz stronę właściwości **Analiza kodu** .

1. Zaznacz pole wyboru **Włącz analizę kodu podczas kompilacji** . Wybierz **przycisk OK** , aby zapisać zmiany.

::: moniker-end

### <a name="to-correct-the-source-code-annotation-warnings-in-annotationc"></a>Aby poprawić ostrzeżenia adnotacji kodu źródłowego w adnotacji. c

1. Kompiluj ponownie projekt adnotacji.

1. W menu **kompilacja** wybierz polecenie **Uruchom analizę kodu w adnotacjach**.

1. W **Lista błędów**kliknij dwukrotnie następujące ostrzeżenie:

     C6011: wyłuskanie wskaźnika o wartości NULL "newNode".

     To ostrzeżenie wskazuje, że obiekt wywołujący nie może sprawdzić zwracanej wartości. W takim przypadku wywołanie `AllocateNode` może zwracać wartość null. Zobacz plik nagłówkowy Annotations. h dla deklaracji funkcji dla `AllocateNode` .

1. Kursor znajduje się w lokalizacji w pliku Annotation. cpp, w której wystąpiło ostrzeżenie.

1. Aby poprawić to ostrzeżenie, należy użyć instrukcji "If" do przetestowania wartości zwracanej. Kod powinien wyglądać podobnie do następującego kodu:

   ```cpp
   LinkedList* newNode = AllocateNode();
   if (nullptr != newNode)
   {
       newNode->data = value;
       newNode->next = 0;
       node->next = newNode;
   }
   ```

1. Kompiluj ponownie projekt adnotacji.

     Projekt kompiluje się bez żadnych ostrzeżeń lub błędów.

## <a name="use-source-code-annotation-to-discover-more-issues"></a>Użyj adnotacji kodu źródłowego, aby poznać więcej problemów

### <a name="to-use-source-code-annotation"></a>Aby użyć adnotacji kodu źródłowego

1. Dodawanie adnotacji do parametrów formalnych i zwracanej wartości funkcji `AddTail` wskazującej, że wartości wskaźnika mogą mieć wartość null:

   ```cpp
   _Ret_maybenull_ LinkedList* AddTail(_Maybenull_ LinkedList* node, int value)
   ```

1. W menu **kompilacja** wybierz polecenie **Uruchom analizę kodu w rozwiązaniu**.

1. W **Lista błędów**kliknij dwukrotnie następujące ostrzeżenie:

     C6011: odwołuje się do "Node" wskaźnika o wartości NULL.

     To ostrzeżenie wskazuje, że węzeł, który przeszedł do funkcji, może mieć wartość null.

1. Aby poprawić to ostrzeżenie, należy użyć instrukcji "If" na początku funkcji, aby przetestować przekazaną wartość. Kod powinien wyglądać podobnie do następującego kodu:

   ```cpp
   if (nullptr == node)
   {
        return nullptr;
   }
   ```

1. W menu **kompilacja** wybierz polecenie **Uruchom analizę kodu w rozwiązaniu**.

     Projekt teraz kompiluje się bez żadnych ostrzeżeń lub błędów.

## <a name="see-also"></a>Zobacz także

[Przewodnik: Analizowanie kodu zarządzanego pod kątem wad kodu](/visualstudio/code-quality/walkthrough-analyzing-managed-code-for-code-defects)\
[Analiza kodu C/C++](../code-quality/code-analysis-for-c-cpp-overview.md)
