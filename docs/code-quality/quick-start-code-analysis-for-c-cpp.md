---
title: 'Szybki start: analiza kodu C/C++'
description: Uruchom analizę statyczną C++ w kodzie w programie Visual Studio, aby wykrywać typowe problemy z kodowaniem i wady.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- C/C++ code analysis
- code analysis,C/C++
ms.openlocfilehash: 5ee8f702ddf489732f664ae73eed75b18dc46e86
ms.sourcegitcommit: 7bea0420d0e476287641edeb33a9d5689a98cb98
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/17/2020
ms.locfileid: "77418782"
---
# <a name="quickstart-code-analysis-for-cc"></a>Szybki start: analiza kodu C/C++

Jakość aplikacji można poprawić, uruchamiając analizę kodu regularnie w języku C lub C++ kodzie. Może to pomóc w znalezieniu typowych problemów, naruszeniu dobrych rozwiązań programistycznych lub wad, które trudno wykryć poprzez testowanie. Ostrzeżenia analizy kodu różnią się od błędów i ostrzeżeń, ponieważ analiza kodu szuka wzorców konkretnego kodu, które są prawidłowe, ale nadal można tworzyć problemy dla Ciebie lub innych osób używających Twojego kodu.

## <a name="configure-rule-sets-for-a-project"></a>Konfigurowanie zestawów reguł dla projektu

1. W **Eksplorator rozwiązań**Otwórz menu skrótów dla nazwy projektu, a następnie wybierz polecenie **Właściwości**.

1. Opcjonalnie na listach **Konfiguracja** i **platforma** wybierz konfigurację kompilacji i platformę docelową.

1. Aby uruchomić analizę kodu za każdym razem, gdy projekt zostanie skompilowany przy użyciu wybranej konfiguracji, zaznacz pole wyboru **Włącz analizę kodu podczas kompilacji** . Możesz również ręcznie uruchomić analizę kodu, otwierając menu **Analizuj** , a następnie wybierając polecenie **Uruchom analizę kodu na** *ProjectName* lub **uruchomić analizę kodu dla pliku**.

1. Wybierz [zestaw reguł](using-rule-sets-to-specify-the-cpp-rules-to-run.md) , którego chcesz użyć, lub Utwórz [niestandardowy zestaw reguł](using-rule-sets-to-specify-the-cpp-rules-to-run.md#to-create-a-rule-set-in-a-text-editor). Jeśli używasz LLVM/Clang-CL, zobacz [using Clang-uporządkowanego in Visual Studio](../code-quality/clang-tidy.md) , aby skonfigurować opcje analizy Clang-uporządkowanego.

### <a name="standard-cc-rule-sets"></a>Standardowe C/C++ zestawy reguł

Program Visual Studio zawiera dwa standardowe zestawy reguł dla kodu natywnego:

|Zestaw reguł|Opis|
|--------------|-----------------|
|Minimalne zalecane reguły natywne firmy Microsoft|Ten zestaw reguł dotyczy najważniejszych problemów w kodzie natywnym, w tym potencjalnych luk w zabezpieczeniach i awarii aplikacji. Ten zestaw reguł powinien być dołączany do każdego niestandardowego zestawu reguł tworzonego dla projektów natywnych.|
|Zalecane reguły natywne firmy Microsoft|Ten zestaw reguł obejmuje szeroki zakres problemów. Zawiera wszystkie reguły w minimalnych zalecanych regułach firmy Microsoft w języku macierzystym.|

## <a name="run-code-analysis"></a>Uruchom analizę kodu

Na stronie Analiza kodu na stronie właściwości projektu można skonfigurować analizę kodu, która będzie uruchamiana za każdym razem, gdy kompilujesz projekt. Możesz również ręcznie uruchomić analizę kodu.

Aby uruchomić analizę kodu w rozwiązaniu:

- W menu **kompilacja** wybierz polecenie **Uruchom analizę kodu w rozwiązaniu**.

Aby uruchomić analizę kodu w projekcie:

1. W Eksplorator rozwiązań wybierz nazwę projektu.

1. W menu **kompilacja** wybierz polecenie **Uruchom analizę kodu dla** *nazwy projektu*.

Aby uruchomić analizę kodu dla pliku:

1. W Eksplorator rozwiązań wybierz nazwę pliku.

1. W menu **kompilacja** wybierz polecenie **Uruchom analizę kodu dla pliku** lub naciśnij **klawisze Ctrl + Shift + Alt + F7**.

   Projekt lub rozwiązanie zostały skompilowane i zostanie uruchomiona Analiza kodu. Wyniki pojawiają się w Lista błędów.

## <a name="analyze-and-resolve-code-analysis-warnings"></a>Analizowanie i rozwiązywanie ostrzeżeń dotyczących analizy kodu

Aby przeanalizować określone ostrzeżenie, wybierz tytuł ostrzeżenia w Lista błędów. Ostrzeżenie zostanie rozwinięte, aby wyświetlić dodatkowe informacje o problemie. Gdy jest to możliwe, analiza kodu wyświetla numery wierszy i logikę analizy, które doprowadziły do ostrzeżenia. Aby uzyskać szczegółowe informacje o ostrzeżeniu, w tym o możliwych rozwiązaniach problemu, wybierz identyfikator ostrzeżenia, aby wyświetlić odpowiedni temat pomocy online.

Po wybraniu ostrzeżenia wiersz kodu, który spowodował ostrzeżenie, jest wyróżniony w edytorze kodu programu Visual Studio.

Po zrozumieniu problem można rozwiązać, w kodzie. Następnie ponownie uruchom analizę kodu, aby upewnić się, że ostrzeżenie nie pojawia się już w Lista błędów i że poprawka nie zgłosiła żadnych nowych ostrzeżeń.

## <a name="suppress-code-analysis-warnings"></a>Pomiń ostrzeżenia analizy kodu

Istnieją terminy, gdy można zdecydować, Rezygnacja z naprawiania ostrzeżenie analizy kodu. Można zdecydować, rozpoznawanie ostrzeżenia wymaga zbyt dużo nagrywanie względem prawdopodobieństwo wystąpienia problemu w implementacji rzeczywistych swój kod. Lub może być uważa, że analizy, który jest używany w ostrzeżenia jest nieodpowiedni dla określonego kontekstu. Możesz pominąć poszczególne ostrzeżenia, aby nie były wyświetlane w Lista błędów.

### <a name="to-suppress-a-warning"></a>Aby pominąć ostrzeżenie

1. Jeśli szczegółowe informacje nie są wyświetlane, wybierz tytuł ostrzeżenia, aby go rozwinąć.

1. Wybierz łącze **Akcje** u dołu ostrzeżenia.

1. Wybierz pozycję **Pomiń komunikat** , a następnie wybierz pozycję **w polu Źródło**.

   Pomijanie komunikatu powoduje wstawienie `#pragma warning (disable:[warning ID])`, który pomija Ostrzeżenie dla wiersza kodu.

## <a name="create-work-items-for-code-analysis-warnings"></a>Utwórz elementy robocze dla ostrzeżeń analizy kodu

Za pomocą funkcji śledzenia elementów roboczych można rejestrować usterki w programie Visual Studio. Aby użyć tej funkcji, należy nawiązać połączenie z wystąpieniem Team Foundation Server.

### <a name="to-create-a-work-item-for-one-or-more-cc-code-warnings"></a>Aby utworzyć element roboczy dla co najmniej jednego ostrzeżenia C/C++ Code

1. W Lista błędów rozwiń i wybierz ostrzeżenia

1. W menu skrótów dla ostrzeżeń wybierz polecenie **Utwórz element roboczy**, a następnie wybierz typ elementu pracy.

1. Program Visual Studio tworzy pojedynczy element roboczy dla wybranych ostrzeżeń i wyświetla element roboczy w oknie dokumentu IDE.

1. Dodaj wszelkie dodatkowe informacje, a następnie wybierz pozycję **Zapisz element roboczy**.

## <a name="search-and-filter-code-analysis-results"></a>Wyszukiwanie i filtrowanie wyników analizy kodu

Możesz wyszukiwać długim spisem komunikaty ostrzegawcze i filtrować ostrzeżeń w rozwiązaniach dotyczących wielu projektów.

- **Aby filtrować ostrzeżenia według tytułu lub identyfikatora ostrzeżenia**: Wprowadź słowo kluczowe w polu wyszukiwania.

- **Aby filtrować ostrzeżenia według ważności**: domyślnie komunikaty analizy kodu są przypisywane ważności **ostrzeżenia**. Można przypisać ważność co najmniej jednego komunikatu jako **błąd** w niestandardowym zestawie reguł. W kolumnie **ważność** **Lista błędów**wybierz strzałkę listy rozwijanej, a następnie ikonę filtru. Wybierz **Ostrzeżenie** lub **błąd** , aby wyświetlić tylko te komunikaty, do których przypisano odpowiednią ważność. Wybierz **pozycję Zaznacz wszystko** , aby wyświetlić wszystkie komunikaty.

## <a name="see-also"></a>Zobacz też

- [Analiza kodu dla języka C/C++](../code-quality/code-analysis-for-c-cpp-overview.md)
