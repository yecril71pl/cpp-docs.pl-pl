---
title: 'Przewodnik: Analizowanie kodu C/C++ pod kątem wad'
description: Pokazuje, jak używać analizy kodu z microsoft C++ w programie Visual Studio.
ms.date: 04/14/2020
ms.topic: conceptual
helpviewer_keywords:
- C/C++, code analysis
- code analysis, walkthroughs
- code, analyzing C/C++
- code analysis tool, walkthroughs
ms.openlocfilehash: fe9b3775199b2a18cf940b99e87852350f1fbea9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370218"
---
# <a name="walkthrough-analyzing-cc-code-for-defects"></a>Przewodnik: Analizowanie kodu C/C++ pod kątem wad

W tym przewodniku pokazano, jak analizować kod C/C++ dla potencjalnych wad kodu. Używa narzędzi analizy kodu dla kodu C/C++.

W tym instruktażu:

- Uruchom analizę kodu na kod natywny.
- Analizowanie ostrzeżeń o wadach kodu.
- Potraktuj ostrzeżenie jako błąd.
- Dodawanie adnotacji do kodu źródłowego w celu poprawy analizy wad kodu.

## <a name="prerequisites"></a>Wymagania wstępne

- Kopia próbki [CppDemo](../code-quality/demo-sample.md).
- Podstawowa wiedza na temat C/C++.

## <a name="run-code-analysis-on-native-code"></a>Uruchamianie analizy kodu na kodzie macierzystym

### <a name="to-run-code-defect-analysis-on-native-code"></a>Aby uruchomić analizę wad kodu na kod natywny

::: moniker range=">=vs-2019"

1. Otwórz rozwiązanie CppDemo w programie Visual Studio.

     Rozwiązanie CppDemo wypełnia teraz **Solution Explorer**.

1. W menu **Kompilacja** wybierz polecenie **Odbuduj rozwiązanie**.

     Rozwiązanie jest budowane bez żadnych błędów lub ostrzeżeń.

1. W **Eksploratorze rozwiązań**wybierz projekt CodeDefects.

1. W menu **Projekt** wybierz polecenie **Właściwości**.

     Zostanie wyświetlone okno dialogowe **Strony właściwości CodeDefects.**

1. Wybierz stronę właściwości **Analiza kodu.**

1. Zmień właściwość **Włącz analizę kodu na kompilacji na** **Tak**. Wybierz **przycisk OK,** aby zapisać zmiany.

1. Odbuduj projekt CodeDefects.

     Ostrzeżenia dotyczące analizy kodu są wyświetlane w oknie **Lista błędów.**

::: moniker-end

::: moniker range="<=vs-2017"

1. Otwórz rozwiązanie CppDemo w programie Visual Studio.

     Rozwiązanie CppDemo wypełnia teraz **Solution Explorer**.

1. W menu **Kompilacja** wybierz polecenie **Odbuduj rozwiązanie**.

     Rozwiązanie jest budowane bez żadnych błędów lub ostrzeżeń.

     > [!NOTE]
     > W programie Visual Studio 2017 może `E1097 unknown attribute "no_init_all"` pojawić się fałszywe ostrzeżenie w silniku IntelliSense. Możesz bezpiecznie zignorować to ostrzeżenie.

1. W **Eksploratorze rozwiązań**wybierz projekt CodeDefects.

1. W menu **Projekt** wybierz polecenie **Właściwości**.

     Zostanie wyświetlone okno dialogowe **Strony właściwości CodeDefects.**

1. Wybierz stronę właściwości **Analiza kodu.**

1. Zaznacz pole wyboru **Włącz analizę kodu na kompilacji.** Wybierz **przycisk OK,** aby zapisać zmiany.

1. Odbuduj projekt CodeDefects.

     Ostrzeżenia dotyczące analizy kodu są wyświetlane w oknie **Lista błędów.**

::: moniker-end

### <a name="to-analyze-code-defect-warnings"></a>Aby przeanalizować ostrzeżenia o wadach kodu

1. W menu **Widok** wybierz polecenie **Lista błędów**.

     Ten element menu może nie być widoczny. To zależy od profilu dewelopera wybranego w programie Visual Studio. Może być trzeba wskazać **inne okna** w menu **Widok,** a następnie wybierz pozycję **Lista błędów**.

1. W oknie **Lista błędów** kliknij dwukrotnie następujące ostrzeżenie:

     C6230: Niejawne rzutowanie między różnymi typami semantycznie: przy użyciu HRESULT w kontekście logicznym.

     Edytor kodu wyświetla wiersz, który spowodował `bool ProcessDomain()`ostrzeżenie wewnątrz funkcji . To ostrzeżenie wskazuje, `HRESULT` że a jest używany w instrukcji "if", w której oczekiwany jest wynik logiczny. Zazwyczaj jest to błąd, ponieważ `S_OK` po powrocie HRESULT z funkcji wskazuje na sukces, ale po przekonwertowaniu na wartość logiczną, na `false`które jest oceniana.

1. Popraw to ostrzeżenie, `SUCCEEDED` używając makra, `true` które `HRESULT` konwertuje na wartość zwracaną wskazującą sukces. Kod powinien przypominać następujący kod:

   ```cpp
   if (SUCCEEDED(ReadUserAccount()))
   ```

1. Na **liście błędów**kliknij dwukrotnie następujące ostrzeżenie:

     C6282: Niepoprawny operator: przypisanie stałej w kontekście logicznym. Zamiast tego należy rozważyć użycie '=='.

1. Popraw to ostrzeżenie, testując równość. Kod powinien wyglądać podobnie do następującego kodu:

   ```cpp
   if ((len == ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != L'\\'))
   ```

1. Popraw pozostałe ostrzeżenia C6001 na **liście błędów,** inicjując `i` i `j` do 0.

1. Odbuduj projekt CodeDefects.

     Projekt tworzy bez żadnych ostrzeżeń lub błędów.

## <a name="correct-source-code-annotation-warnings"></a>Prawidłowe ostrzeżenia o adnotacji kodu źródłowego

### <a name="to-enable-the-source-code-annotation-warnings-in-annotationc"></a>Aby włączyć ostrzeżenia o adnotacji kodu źródłowego w adnotacji.c

::: moniker range=">=vs-2019"

1. W Eksploratorze rozwiązań wybierz projekt Adnotacje.

1. W menu **Projekt** wybierz polecenie **Właściwości**.

     Zostanie wyświetlone okno dialogowe **Strony właściwości adnotacji.**

1. Wybierz stronę właściwości **Analiza kodu.**

1. Zmień właściwość **Włącz analizę kodu na kompilacji na** **Tak**. Wybierz **przycisk OK,** aby zapisać zmiany.

::: moniker-end

::: moniker range="<=vs-2017"

1. W Eksploratorze rozwiązań wybierz projekt Adnotacje.

1. W menu **Projekt** wybierz polecenie **Właściwości**.

     Zostanie wyświetlone okno dialogowe **Strony właściwości adnotacji.**

1. Wybierz stronę właściwości **Analiza kodu.**

1. Zaznacz pole wyboru **Włącz analizę kodu na kompilacji.** Wybierz **przycisk OK,** aby zapisać zmiany.

::: moniker-end

### <a name="to-correct-the-source-code-annotation-warnings-in-annotationc"></a>Aby poprawić ostrzeżenia o adnotacji kodu źródłowego w adnotacji.c

1. Odbuduj projekt Adnotacje.

1. W menu **Kompilacja** wybierz polecenie **Uruchom analizę kodu w adnotacje**.

1. Na **liście błędów**kliknij dwukrotnie następujące ostrzeżenie:

     C6011: Dereferencing NULL wskaźnik "newNode".

     To ostrzeżenie wskazuje, że błąd wywołującego, aby sprawdzić wartość zwracaną. W takim przypadku wywołanie `AllocateNode` może zwrócić wartość NULL. Zobacz plik nagłówka annotations.h dla `AllocateNode`deklaracji funkcji dla .

1. Kursor znajduje się w lokalizacji w pliku adnotations.cpp, w którym wystąpiło ostrzeżenie.

1. Aby poprawić to ostrzeżenie, należy użyć instrukcji "if", aby przetestować wartość zwracaną. Kod powinien przypominać następujący kod:

   ```cpp
   LinkedList* newNode = AllocateNode();
   if (nullptr != newNode)
   {
       newNode->data = value;
       newNode->next = 0;
       node->next = newNode;
   }
   ```

1. Odbuduj projekt Adnotacje.

     Projekt tworzy bez żadnych ostrzeżeń lub błędów.

## <a name="use-source-code-annotation-to-discover-more-issues"></a>Użyj adnotacji kodu źródłowego, aby wykryć więcej problemów

### <a name="to-use-source-code-annotation"></a>Aby użyć adnotacji kodu źródłowego

1. Adnotacje parametry formalne i `AddTail` zwraca wartość funkcji, aby wskazać wartości wskaźnika może być null:

   ```cpp
   _Ret_maybenull_ LinkedList* AddTail(_Maybenull_ LinkedList* node, int value)
   ```

1. W menu **Kompilacja** wybierz polecenie **Uruchom analizę kodu w programie Solution**.

1. Na **liście błędów**kliknij dwukrotnie następujące ostrzeżenie:

     C6011: Dereferencing NULL wskaźnik "węzeł".

     To ostrzeżenie wskazuje, że węzeł przekazany do funkcji może mieć wartość null.

1. Aby poprawić to ostrzeżenie, należy użyć instrukcji "if" na początku funkcji, aby przetestować wartość zdawana. Kod powinien przypominać następujący kod:

   ```cpp
   if (nullptr == node)
   {
        return nullptr;
   }
   ```

1. W menu **Kompilacja** wybierz polecenie **Uruchom analizę kodu w programie Solution**.

     Projekt jest teraz budowany bez żadnych ostrzeżeń i błędów.

## <a name="see-also"></a>Zobacz też

[Przewodnik: Analizowanie kodu zarządzanego pod kątem wad kodu](/visualstudio/code-quality/walkthrough-analyzing-managed-code-for-code-defects)\
[Analiza kodu C/C++](../code-quality/code-analysis-for-c-cpp-overview.md)
