---
title: Najlepsze praktyki w zakresie zabezpieczeń dla C++
ms.date: 05/08/2018
f1_keywords:
- securitybestpracticesVC
helpviewer_keywords:
- Visual C++, security
- security [C++]
- security [C++], best practices
ms.assetid: 86acaccf-cdb4-4517-bd58-553618e3ec42
ms.openlocfilehash: 81a15f7a34ebe6c4c101932074c63cb1c7f7fd26
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/11/2019
ms.locfileid: "57742470"
---
# <a name="security-best-practices-for-c"></a>Najlepsze praktyki w zakresie zabezpieczeń dla C++

Ten artykuł zawiera informacje dotyczące narzędzi zabezpieczeń i praktyki. Korzystanie z nich nie oznacza, że aplikacje odporna na ataki, ale to sprawia, że zakończonego pomyślnie ataku mniej prawdopodobne.

## <a name="visual-c-security-features"></a>Funkcje zabezpieczeń w programie Visual C++

Te funkcje zabezpieczeń są wbudowane w kompilator języka Visual C++ i konsolidatora:

[/guard (Włącz ochronę przepływu sterowania)](../build/reference/guard-enable-control-flow-guard.md)<br/>
Powoduje, że kompilator analizować przepływ kontroli dla pośredniego rozmów w czasie kompilacji, a następnie Wstaw kod, aby sprawdzić elementy docelowe w czasie wykonywania.

[/GS (Sprawdzanie zabezpieczeń bufora)](../build/reference/gs-buffer-security-check.md)<br/>
Instruuje kompilator, aby wstawić przepełnienie podczas wykrywania kod do funkcji, które są zagrożone w czasie. Po wykryciu przepełnienie podczas wykonywania została zatrzymana. Domyślnie ta opcja jest włączona.

[/SAFESEH (Obraz ma bezpieczną obsługę wyjątków)](../build/reference/safeseh-image-has-safe-exception-handlers.md)<br/>
Nakazuje programowi łączącemu uwzględnienie w obrazie danych wyjściowych tabeli, która zawiera adres każdy program obsługi wyjątków. W czasie wykonywania system operacyjny używa tej tabeli, aby upewnić się, że programy obsługi wyjątków tylko uprawnionym są wykonywane. Pozwala to zapobiec wykonywania programów obsługi wyjątków, które są wprowadzone przez złośliwych ataków w czasie wykonywania. Domyślnie ta opcja jest wyłączona.

[/ NXCOMPAT](../build/reference/nxcompat.md), [/NXCOMPAT (zgodny z zapobieganiem wykonywaniu danych)](../build/reference/nxcompat-compatible-with-data-execution-prevention.md) te opcje kompilatora i konsolidatora zgodność zapobieganie wykonywaniu danych (DEP). DEP chroni procesora CPU na wykonanie kodowe —.

[/analyze (Analiza kodu)](../build/reference/analyze-code-analysis.md)<br/>
Tę opcję kompilatora aktywuje analizy kodu, który zgłasza potencjalnych problemów z zabezpieczeniami, takich jak przepełnienia buforu, pamięci surowej zainicjowane, wyłuskanie wskaźnika o wartości null i przecieki pamięci. Domyślnie ta opcja jest wyłączona. Aby uzyskać więcej informacji, zobacz [analiza kodu C/C++ — Przegląd](/visualstudio/code-quality/code-analysis-for-c-cpp-overview).

[/DYNAMICBASE (Korzystaj z randomizacji układu przestrzeni adresowej)](../build/reference/dynamicbase-use-address-space-layout-randomization.md)<br/>
Tę opcję konsolidatora umożliwia tworzenie obrazu pliku wykonywalnego, który może zostać załadowany w różnych lokalizacjach w pamięci na początku wykonywania. Ta opcja powoduje lokalizacji stosu w pamięci znacznie mniej przewidywalne.

## <a name="security-enhanced-crt"></a>CRT z rozszerzonymi zabezpieczeniami

Biblioteka środowiska uruchomieniowego C (CRT) został uzupełniony obejmujący bezpieczne wersje funkcji, które stanowić zagrożenia bezpieczeństwa — na przykład unchecked `strcpy` ciągów funkcji kopiowania. Ponieważ starsze, niezabezpieczone wersje tych funkcji są przestarzałe, spowodują ostrzeżenia kompilacji. Zachęcamy do korzystania z bezpieczne wersje tych funkcji CRT zamiast pomijanie ostrzeżeń kompilacji. Aby uzyskać więcej informacji, zobacz [funkcje zabezpieczeń w CRT](../c-runtime-library/security-features-in-the-crt.md).

## <a name="safeint-library"></a>Biblioteka SafeInt

[Biblioteka SafeInt](../windows/safeint-library.md) pomaga uniknąć przepełnienia liczby całkowitej i inne możliwe do wykorzystania błędy, które mogą wystąpić, gdy aplikacja wykonuje operacje matematyczne. `SafeInt` Biblioteka zawiera [safeint — klasa](../windows/safeint-class.md), [safeintexception — klasa](../windows/safeintexception-class.md)oraz kilka [safeint — funkcje](../windows/safeint-functions.md).

`SafeInt` Klasy chroni przed przepełnienie liczby całkowitej i wykorzystuje dzielenie przez zero. Służy do obsługi porównanie wartości o różnych typach. Udostępnia dwie zasady obsługi błędów. Domyślna zasada dotyczy `SafeInt` klasy, aby zgłosić `SafeIntException` klasy wyjątku do raportu, dlaczego nie można ukończyć operacji matematycznych. Drugie zasady jest `SafeInt` klasy, aby zatrzymać wykonywanie programów. Można również definiować niestandardowe zasady.

Każdy `SafeInt` funkcja zapewnia ochronę jednej operacji matematycznych sprawność po błędzie kończona. Dwa różne rodzaje parametrów można użyć bez konwertowania go na potrzeby tego samego typu. Aby chronić wiele operacji matematycznych, użyj `SafeInt` klasy.

## <a name="checked-iterators"></a>Zaznaczone iteratory

Iterator sprawdzony wymusza granice kontenera. Domyślnie gdy sprawdzonego iteratora jest poza zakresem, go generuje wyjątek i kończy działanie programu. Iteratora sprawdzanego zapewnia innych poziomów odpowiedzi, które są zależne od wartości, które są przypisane do preprocesora definiuje takie jak  **\_bezpiecznego\_SCL\_ZGŁASZA** i  **\_ITERATORA\_debugowania\_poziom**. Np. w  **\_ITERATORA\_debugowania\_LEVEL = 2**, sprawdzonego iteratora zapewnia kompleksowe poprawność sprawdza, czy w trybie debugowania, które są udostępniane za pomocą potwierdzenia. Aby uzyskać więcej informacji, zobacz [Checked Iterators](../standard-library/checked-iterators.md) i [ \_ITERATORA\_debugowania\_poziom](../standard-library/iterator-debug-level.md).

## <a name="code-analysis-for-managed-code"></a>Analizowanie kodu zarządzanego

Analiza kodu dla kodu zarządzanego, znany także jako FxCop, sprawdza, czy zestawy dla zgodności do środowiska.NET Framework — zalecenia dotyczące projektowania. FxCop analizuje kod i metadane w każdym zestawie pod kątem defektów w następujących obszarach:

- Projekt biblioteki

- Lokalizacja

- Konwencje nazewnictwa

- Wydajność

- Zabezpieczenia

## <a name="windows-application-verifier"></a>Weryfikator aplikacji Windows

[Weryfikator aplikacji (użycie narzędzia AppVerifier)](/windows-hardware/drivers/debugger/application-verifier
) może pomóc w zidentyfikowaniu potencjalnych problemów ze zgodnością, stabilności i zabezpieczeń aplikacji.

Użycie narzędzia AppVerifier monitoruje, jak aplikacja używa systemu operacyjnego. Jego obserwuje systemu plików, rejestru, pamięci i interfejsów API, gdy aplikacja jest uruchomiona i zaleca się kod źródłowy poprawki dotyczące problemów, które go znajdujący.

Umożliwia użycie narzędzia AppVerifier do:

- Test na potencjalne błędy zgodności aplikacji, które są spowodowane przez typowe błędy programowania.

- Przeanalizuj aplikację w przypadku problemów związanych z pamięcią.

- Zidentyfikuj potencjalne problemy w aplikacji.

## <a name="windows-user-accounts"></a>Konta użytkowników Windows

Przy użyciu Windows kont użytkowników należących do deweloperów ujawnia grupy Administratorzy i--przez rozszerzenie — klienci na zagrożenia bezpieczeństwa. Aby uzyskać więcej informacji, zobacz [uruchamianie jako członek grupy Użytkownicy](running-as-a-member-of-the-users-group.md) i [jak konta użytkownika kontroli (UAC) wpływa na aplikacji](how-user-account-control-uac-affects-your-application.md).

## <a name="guidance-for-speculative-execution-side-channels"></a>Wskazówki dotyczące spekulacyjnego kanały po stronie wykonywania

Aby uzyskać informacje dotyczące sposobu identyfikowania i łagodzi skutki związanego z wykonywaniem spekulatywnym po stronie kanału sprzętowych luk w zabezpieczeniach oprogramowania C++, zobacz [wskazówki dla deweloperów C++ dla kanałów po stronie wykonywania spekulacyjne](developer-guidance-speculative-execution.md).

## <a name="see-also"></a>Zobacz także

<xref:System.Security> <br/>
[Zabezpieczenia](/dotnet/standard/security/index)<br/>
[Jak kontrola konta użytkownika (UAC) wpływa na aplikację?](how-user-account-control-uac-affects-your-application.md)
