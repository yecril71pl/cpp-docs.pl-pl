---
title: Funkcje zabezpieczeń w CRT
ms.date: 11/04/2016
f1_keywords:
- _CRT_SECURE_NO_DEPRECATE
- _CRT_NONSTDC_NO_WARNINGS
- _CRT_SECURE_NO_WARNINGS
helpviewer_keywords:
- security deprecation warnings [C++]
- CRT_NONSTDC_NO_DEPRECATE
- buffers [C++], buffer overruns
- deprecation warnings (security-related), disabling
- _CRT_NONSTDC_NO_WARNINGS
- security [CRT]
- _CRT_SECURE_NO_WARNINGS
- _CRT_NONSTDC_NO_DEPRECATE
- _CRT_SECURE_NO_DEPRECATE
- security-enhanced CRT
- CRT_SECURE_NO_WARNINGS
- CRT_SECURE_NO_DEPRECATE
- deprecation warnings (security-related)
- buffer overruns
- CRT_NONSTDC_NO_WARNINGS
- CRT, security enhancements
- parameters [C++], validation
ms.assetid: d9568b08-9514-49cd-b3dc-2454ded195a3
ms.openlocfilehash: 1b42c766a7b75cb3f4d5c20d715968905d529d04
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81361006"
---
# <a name="security-features-in-the-crt"></a>Funkcje zabezpieczeń w CRT

Wiele starych funkcji CRT ma nowsze, bezpieczniejsze wersje. Jeśli istnieje funkcja secure, starsza, mniej bezpieczna wersja jest oznaczona `_s` jako przestarzała, a nowa wersja ma sufiks ("secure").

W tym kontekście "przestarzałe" oznacza tylko, że użycie funkcji nie jest zalecane; nie oznacza, że funkcja jest zaplanowane do usunięcia z CRT.

Bezpieczne funkcje nie zapobiegają błędom zabezpieczeń ani ich nie korygują; raczej łapią błędy, gdy wystąpią. Przeprowadzają dodatkowe kontrole warunków błędu, a w przypadku błędu wywołują program obsługi błędów (patrz [Sprawdzanie poprawności parametrów).](../c-runtime-library/parameter-validation.md)

Na przykład `strcpy` funkcja nie ma możliwości informowania, czy ciąg, który jest kopiowany jest zbyt duży dla buforu docelowego. Jednak jego bezpieczny `strcpy_s`odpowiednik, , przyjmuje rozmiar buforu jako parametr, dzięki czemu można określić, czy nastąpi przepełnienie buforu. Jeśli używasz `strcpy_s` do kopiowania jedenaście znaków do buforu dziesięciu znaków, jest to błąd z Twojej strony; `strcpy_s` nie można poprawić błędu, ale może wykryć błąd i poinformować użytkownika, wywołując nieprawidłowy program obsługi parametrów.

## <a name="eliminating-deprecation-warnings"></a>Eliminowanie ostrzeżeń o usuwaniu

Istnieje kilka sposobów, aby wyeliminować ostrzeżenia o deprecation dla starszych, mniej bezpiecznych funkcji. Najprostszym jest po `_CRT_SECURE_NO_WARNINGS` prostu zdefiniować lub użyć pragmy [ostrzegawczej.](../preprocessor/warning.md) Albo wyłączy ostrzeżenia o uszczukaniu, ale oczywiście nadal istnieją problemy z zabezpieczeniami, które spowodowały ostrzeżenia. O wiele lepiej jest pozostawić ostrzeżenia o nadszyfrywanie włączone i skorzystać z nowych funkcji zabezpieczeń CRT.

W języku C++ najprostszym sposobem, aby to zrobić, jest użycie [bezpiecznego przeciążenia szablonu](../c-runtime-library/secure-template-overloads.md), co w wielu przypadkach wyeliminuje ostrzeżenia o deprecation, zastępując wywołania przestarzałych funkcji wywołaniem nowych bezpiecznych wersji tych funkcji. Rozważmy na przykład to przestarzałe wywołanie: `strcpy`

```
char szBuf[10];
strcpy(szBuf, "test"); // warning: deprecated
```

Definiowanie `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` jako 1 eliminuje ostrzeżenie, `strcpy` zmieniając `strcpy_s`wywołanie do , co zapobiega przekroczeniu buforu. Aby uzyskać więcej informacji, zobacz [Bezpieczne przeciążenia szablonu](../c-runtime-library/secure-template-overloads.md).

W przypadku tych przestarzałych funkcji bez przeciążeń bezpiecznego szablonu zdecydowanie należy rozważyć ręczne aktualizowanie kodu w celu użycia bezpiecznych wersji.

Innym źródłem ostrzeżeń o wycofanie, niezwiązane z zabezpieczeniami, są funkcje POSIX. Zastąp nazwy funkcji POSIX ich standardowymi odpowiednikami (na przykład zmień [dostęp](../c-runtime-library/reference/access-crt.md) do [_access)](../c-runtime-library/reference/access-waccess.md)lub `_CRT_NONSTDC_NO_WARNINGS`wyłącz ostrzeżenia o posix związanych z poniżaniem, definiując . Aby uzyskać więcej informacji, zobacz [Zgodność](compatibility.md).

## <a name="additional-security-features"></a>Dodatkowe funkcje zabezpieczeń

Niektóre funkcje zabezpieczeń są następujące:

- `Parameter Validation`. Parametry przekazywane do funkcji CRT są sprawdzane, zarówno w bezpiecznych funkcjach, jak i w wielu istniejących wersjach funkcji. Te weryfikacje obejmują:

  - Sprawdzanie wartości **NULL** przekazanych do funkcji.

  - Sprawdzanie wyliczonych wartości pod kątem ważności.

  - Sprawdzanie, czy wartości integralne znajdują się w prawidłowych zakresach.

- Aby uzyskać więcej informacji, zobacz [Sprawdzanie poprawności parametrów](../c-runtime-library/parameter-validation.md).

- Program obsługi dla nieprawidłowych parametrów jest również dostępny dla dewelopera. Gdy napotkanie nieprawidłowy parametr, zamiast potwierdzenia i zamykania aplikacji, CRT zapewnia sposób, aby sprawdzić te problemy z [_set_invalid_parameter_handler, _set_thread_local_invalid_parameter_handler](../c-runtime-library/reference/set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md) funkcji.

- `Sized Buffers`. Funkcje bezpieczne wymagają, aby rozmiar buforu był przekazywany do dowolnej funkcji, która zapisuje do buforu. Bezpieczne wersje sprawdzają, czy bufor jest wystarczająco duży przed zapisaniem do niego, co pomaga uniknąć niebezpiecznych błędów przepełnienia buforu, które mogą umożliwić wykonanie złośliwego kodu. Te funkcje `errno` zwykle zwracają typ kodu błędu i wywołać nieprawidłowy program obsługi parametrów, jeśli rozmiar buforu jest zbyt mały. Funkcje odczytywane z buforów wejściowych, takie jak `gets`, mają bezpieczne wersje, które wymagają określenia maksymalnego rozmiaru.

- `Null termination`. Niektóre funkcje, które opuściły potencjalnie nie zakończone ciągi mają bezpieczne wersje, które zapewniają, że ciągi są poprawnie zakończone zerem.

- `Enhanced error reporting`. Bezpieczne funkcje zwracają kody błędów z większą liczoną niż dostępna w istniejących funkcjach. Bezpieczne funkcje i wiele istniejących funkcji teraz `errno` ustawić i `errno` często zwraca typ kodu, jak również, aby zapewnić lepsze raportowanie błędów.

- `Filesystem security`. Bezpieczne interfejsy WE/Wy plików obsługują bezpieczny dostęp do plików w przypadku domyślnym.

- `Windows security`. Bezpieczne interfejsy API procesów wymuszają zasady zabezpieczeń i umożliwiają określanie list ACL.

- `Format string syntax checking`. Nieprawidłowe ciągi są wykrywane, na przykład `printf` przy użyciu niepoprawnych znaków pola typu w ciągach formatu.

## <a name="see-also"></a>Zobacz też

[Walidacja parametru](../c-runtime-library/parameter-validation.md)<br/>
[Bezpieczne przeciążenia szablonu](../c-runtime-library/secure-template-overloads.md)<br/>
[Funkcje biblioteki CRT](../c-runtime-library/crt-library-features.md)
