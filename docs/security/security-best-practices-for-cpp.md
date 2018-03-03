---
title: "Najlepsze rozwiązania dotyczące C++ | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- securitybestpracticesVC
dev_langs:
- C++
helpviewer_keywords:
- Visual C++, security
- security [C++]
- security [C++], best practices
ms.assetid: 86acaccf-cdb4-4517-bd58-553618e3ec42
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0f1474f44b81a95c119a405dda8a91db62a08417
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2018
---
# <a name="security-best-practices-for-c"></a>Najlepsze praktyki w zakresie zabezpieczeń dla C++
Ten artykuł zawiera informacje o narzędziach zabezpieczeń i rozwiązań. Ich użycie nie oznacza, że aplikacje odporna na ataki, ale ułatwia udanych ataków rzadziej.  
  
## <a name="visual-c-security-features"></a>Funkcje zabezpieczeń w programie Visual C++  
 Te funkcje zabezpieczeń są wbudowane w kompilatora Visual C++ i linker:  
  
 [/ GUARD (Włącz ochronę przepływu sterowania)](../build/reference/guard-enable-control-flow-guard.md)  
 Powoduje, że kompilator w celu analizowania przepływ kontroli dla pośredniego rozmów w czasie kompilacji, a następnie Wstaw kod, aby zweryfikować elementy docelowe w czasie wykonywania.  
  
 [/GS (Sprawdzanie zabezpieczeń bufora)](../build/reference/gs-buffer-security-check.md)  
 Instruuje kompilator, aby wstawić kod wykrywania przekroczenie do funkcji, które są zagrożone w czasie. Po wykryciu przekroczenia wykonywania została zatrzymana. Domyślnie ta opcja jest włączona.  
  
 [/ SAFESEH (obraz ma bezpieczną obsługę wyjątków)](../build/reference/safeseh-image-has-safe-exception-handlers.md)  
 Informuje konsolidator, aby dołączyć do obrazu wyjściowego tabelę, która zawiera adres każdy program obsługi wyjątku. W czasie wykonywania system operacyjny używa tej tabeli, aby upewnić się, że programy obsługi wyjątków tylko uprawnionym są wykonywane. Pomaga to zapobiec wykonywania programów obsługi wyjątków, które zostaną wprowadzone złośliwymi atakami w czasie wykonywania. Domyślnie ta opcja jest wyłączona.  
  
 [/ NXCOMPAT](../build/reference/nxcompat.md), [/NXCOMPAT (zgodny z zapobieganiem wykonywaniu danych)](../build/reference/nxcompat-compatible-with-data-execution-prevention.md)  
 Te opcje konsolidatora i kompilatora zgodność zapobiegania wykonywaniu danych (DEP). DEP chroni procesora CPU na wykonanie kodowe —.  
  
 [/ analyze (analiza kodu)](../build/reference/analyze-code-analysis.md)  
 Ta opcja kompilatora aktywuje analizy kodu, który zgłasza potencjalnych problemów z zabezpieczeniami, takich jak przepełnienie buforu, które nie zostały zainicjowane pamięci dereferencji wskaźnika o wartości null i przecieki pamięci. Domyślnie ta opcja jest wyłączona. Aby uzyskać więcej informacji, zobacz [analizy kodu dla C/C++ — omówienie](/visualstudio/code-quality/code-analysis-for-c-cpp-overview).  
  
 [/ DYNAMICBASE (randomizacji układu przestrzeni adresowej Użyj)](../build/reference/dynamicbase-use-address-space-layout-randomization.md)  
 Ta opcja konsolidatora umożliwia tworzenie obrazu wykonywalnego, który może zostać załadowany w różnych lokalizacjach w pamięci na początku wykonywania. Ta opcja powoduje lokalizacji stosu w pamięci znacznie mniej przewidywalne.  
  
## <a name="security-enhanced-crt"></a>CRT z rozszerzonymi zabezpieczeniami  
 C Runtime Library (CRT) ma zostały rozszerzone do uwzględnienia bezpiecznego wersje funkcji, które stanowią zagrożenie bezpieczeństwa — na przykład niezaznaczone `strcpy` ciągu funkcji kopiowania. Ponieważ starszej wersji niezabezpieczone tych funkcji są przestarzałe, spowodują one ostrzeżeń kompilacji. Firma Microsoft zachęca do korzystania z bezpiecznego wersje funkcji CRT zamiast pomijanie ostrzeżeń kompilacji. Aby uzyskać więcej informacji, zobacz [funkcje zabezpieczeń w CRT](../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="safeint-library"></a>Biblioteka SafeInt  
 [Biblioteka SafeInt](../windows/safeint-library.md) pomaga uniknąć przepełnienia całkowitą i innych kończona błędów, które mogą wystąpić, gdy aplikacja wykonuje operacji matematycznych. `SafeInt` Biblioteka zawiera [safeint — klasa](../windows/safeint-class.md), [safeintexception — klasa](../windows/safeintexception-class.md)i kilka [safeint — funkcje](../windows/safeint-functions.md).  
  
 `SafeInt` Klasy chroni przed całkowitą przepełnienie i wykorzystuje dzielenie przez zero. Służy on do obsługi porównanie wartości różnych typów. I udostępnia dwie zasady obsługi błędów. Domyślna zasada jest przeznaczona dla `SafeInt` klasę, aby zgłosić `SafeIntException` klasy wyjątku do raportu, dlaczego nie można ukończyć operacji matematycznych. Drugi zasada jest przeznaczona dla `SafeInt` klasę, aby zatrzymać wykonanie programu. Istnieje również możliwość definiowania niestandardowych zasad.  
  
 Każdy `SafeInt` funkcja uniemożliwia kończona błąd jednej operacji matematycznych. Bez potrzeby konwertowania ich na ten sam typ, można użyć dwóch różnych rodzajów parametrów. Aby chronić wiele operacji matematycznych, użyj `SafeInt` klasy.  
  
## <a name="checked-iterators"></a>Zaznaczone iteratory  
 Checked iteratora wymusza granice kontenera. Domyślnie gdy zaznaczone iteratora jest poza zakresem, go generuje wyjątek i kończy działanie programu. Checked iteratora zapewnia innych poziomach odpowiedzi, które są zależne od wartości, które są przypisane do preprocesora definiuje, takich jak  **\_bezpiecznego\_SCL\_ZGŁASZA** i  **\_ITERATOR\_debugowania\_poziom**. Na przykład na  **\_ITERATORA\_debugowania\_LEVEL = 2**, zaznaczone iteratora zapewnia kompleksowe poprawności sprawdza się w trybie debugowania, które są udostępniane za pomocą potwierdzeń. Aby uzyskać więcej informacji, zobacz [zaznaczone Iteratory](../standard-library/checked-iterators.md) i [ \_ITERATOR\_debugowania\_poziom](../standard-library/iterator-debug-level.md).  
  
## <a name="code-analysis-for-managed-code"></a>Analiza kodu dla zarządzanego kodu  
 Analiza kodu dla kodu zarządzanego, znanej także jako FxCop, sprawdza, czy zestawy dla zgodność ze środowiska.NET Framework wskazówek. FxCop analizę kodu i metadanych w każdym zestawie do sprawdzenia pod względem wad w następujących obszarach:  
  
-   Projekt biblioteki  
  
-   Lokalizacja  
  
-   Konwencje nazewnictwa  
  
-   Wydajność  
  
-   Zabezpieczenia  
  
## <a name="windows-application-verifier"></a>Weryfikator aplikacji systemu Windows  
 Weryfikator aplikacji (użycie narzędzia AppVerifier) może pomóc w identyfikacji potencjalnych problemów ze zgodnością, stabilności i zabezpieczeń aplikacji.  
  
 Użycie narzędzia AppVerifier monitoruje jak aplikacja korzysta z systemu operacyjnego. Go oczekuje systemu plików, rejestru, pamięci, i interfejsów API, podczas gdy aplikacja jest uruchomiona i zaleca kodu źródłowego poprawki dotyczące problemów z jej odkrywa.  
  
 Można użyć narzędzia AppVerifier do:  
  
-   Test na potencjalne błędy zgodności aplikacji, które wynikają z typowych pomyłek programowania.  
  
-   Sprawdź aplikację w przypadku problemów związanych z pamięcią.  
  s
-   Zidentyfikuj potencjalne problemy w aplikacji.  
  
 Użycie narzędzia AppVerifier wchodzi w skład narzędzi zgodności aplikacji, która jest dostępna z [zgodności aplikacji](http://go.microsoft.com/fwlink/p/?linkid=91277) w witrynie TechNet.  
  

## <a name="windows-user-accounts"></a>Konta użytkownika systemu Windows  
 Przy użyciu konta systemu Windows użytkownika należące do deweloperów ujawnia grupy Administratorzy i--przez rozszerzenie — klienci na zagrożenia bezpieczeństwa. Aby uzyskać więcej informacji, zobacz [uruchamianie jako członek grupy Użytkownicy](running-as-a-member-of-the-users-group.md) i [jak (Kontrola konta) dotyczy Twoja aplikacja](how-user-account-control-uac-affects-your-application.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Security>   
 [Zabezpieczeń](/dotnet/standard/security/index)   
 [Jak kontrola konta użytkownika (UAC) wpływa na aplikację?](how-user-account-control-uac-affects-your-application.md)