---
title: Funkcje zabezpieczeń w CRT
description: Omówienie bezpiecznych funkcji CRT w środowisku uruchomieniowym języka Microsoft C.
ms.date: 09/29/2020
ms.topic: conceptual
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
ms.openlocfilehash: 963f5510350aa3be25586811889189d28a5f7b66
ms.sourcegitcommit: 9451db8480992017c46f9d2df23fb17b503bbe74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/30/2020
ms.locfileid: "91589890"
---
# <a name="security-features-in-the-crt"></a>Funkcje zabezpieczeń w CRT

Wiele starych funkcji CRT ma nowsze, bezpieczniejsze wersje. Jeśli istnieje bezpieczna funkcja, Starsza, mniej bezpieczna wersja jest oznaczona jako przestarzała, a nowa wersja ma `_s` sufiks ("Secure").

W tym kontekście "przestarzałe" oznacza użycie funkcji nie jest zalecane. Nie oznacza to, że funkcja jest zaplanowana do usunięcia z CRT.

Funkcje Secure nie uniemożliwiają lub nie korygują błędów zabezpieczeń. Zamiast tego przechwytują błędy, gdy wystąpią. Wykonują dodatkowe sprawdzenia dotyczące warunków błędów. Jeśli wystąpi błąd, wywołuje procedurę obsługi błędów (zobacz [Walidacja parametrów](../c-runtime-library/parameter-validation.md)).

Na przykład `strcpy` Funkcja nie może stwierdzić, czy ciąg, który jest kopiowany jest zbyt duży dla bufora docelowego. Jego bezpieczny odpowiednik, `strcpy_s` , pobiera rozmiar buforu jako parametr. W ten sposób można określić, czy wystąpiło przepełnienie buforu. Jeśli używasz `strcpy_s` do kopiowania 11 znaków do 10-znakowego bufora, który jest błędem w Twojej części; `strcpy_s` nie można poprawić błędu. Ale może wykryć błąd i poinformować Cię o wywołaniu procedury obsługi nieprawidłowego parametru.

## <a name="eliminating-deprecation-warnings"></a>Eliminowanie ostrzeżeń o zaniechaniu

Istnieje kilka sposobów wyeliminowania ostrzeżeń o wycofaniu dla starszych, mniej bezpiecznych funkcji. Najprostszym jest po prostu zdefiniowanie `_CRT_SECURE_NO_WARNINGS` lub użycie dyrektywy pragma [ostrzeżenia](../preprocessor/warning.md) . Spowoduje to wyłączenie ostrzeżeń o zaniechaniu, ale nadal istnieją problemy z zabezpieczeniami, które spowodowały ostrzeżenia. Lepiej jest pozostawić ostrzeżenia o wycofaniu i korzystać z nowych funkcji zabezpieczeń CRT.

W języku C++ Najprostszym sposobem na to jest użycie [przeciążenia bezpiecznego szablonu](../c-runtime-library/secure-template-overloads.md). Spowoduje to wyeliminowanie ostrzeżeń o zaniechaniu w wielu przypadkach przez zamianę wywołań przestarzałych funkcji na wywołania bezpiecznych wersji tych funkcji. Rozważmy na przykład to przestarzałe wywołanie do `strcpy` :

```
char szBuf[10];
strcpy(szBuf, "test"); // warning: deprecated
```

Zdefiniowanie `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` jako 1 eliminuje ostrzeżenie przez zmianę `strcpy` wywołania do `strcpy_s` , co uniemożliwia przekroczenie buforu. Aby uzyskać więcej informacji, zobacz [bezpieczne przeciążenia szablonów](../c-runtime-library/secure-template-overloads.md).

W przypadku tych przestarzałych funkcji bez zabezpieczeń przeciążeń szablonów należy okresowo rozważyć ręczne aktualizowanie kodu w celu używania bezpiecznych wersji.

Innym źródłem ostrzeżeń o zaniechaniu, niezwiązanych z zabezpieczeniami, jest funkcja POSIX. Zamień nazwy funkcji POSIX na ich standardowe odpowiedniki (na przykład zmiana [dostępu](../c-runtime-library/reference/access-crt.md) do [_access](../c-runtime-library/reference/access-waccess.md)) lub Wyłącz ostrzeżenia o zaniechaniu związanym z systemem POSIX przez zdefiniowanie `_CRT_NONSTDC_NO_WARNINGS` . Aby uzyskać więcej informacji, zobacz [zgodność](compatibility.md).

## <a name="additional-security-features"></a>Dodatkowe funkcje zabezpieczeń

Niektóre funkcje zabezpieczeń obejmują:

- `Parameter Validation`. Zabezpiecz funkcje i wiele niezabezpieczonych odpowiedników, sprawdź poprawność parametrów. Sprawdzanie poprawności może obejmować:

  - Sprawdzanie wartości **null** .
  - Sprawdzanie poprawności wyliczanych wartości.
  - Sprawdzanie, czy wartości całkowite znajdują się w prawidłowych zakresach.

- Aby uzyskać więcej informacji, zobacz [Walidacja parametrów](../c-runtime-library/parameter-validation.md).

- Program obsługi dla nieprawidłowych parametrów jest również dostępny dla dewelopera. Gdy funkcja napotka nieprawidłowy parametr, a nie zostanie potwierdzona i zakończona aplikacja, CRT pozwala sprawdzić te problemy za pośrednictwem [_set_invalid_parameter_handler, _set_thread_local_invalid_parameter_handler](../c-runtime-library/reference/set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md).

- `Sized Buffers`. Rozmiar buforu należy przekazać do dowolnej bezpiecznej funkcji, która zapisuje dane w buforze. Bezpieczne wersje sprawdzają, czy bufor jest wystarczająco duży przed zapisem w nim. Pozwala to uniknąć niegroźnych błędów przepełnienia buforu, które mogą pozwolić na wykonanie złośliwego kodu. Te funkcje zwykle zwracają `errno` Kod błędu i wywołują procedurę obsługi nieprawidłowego parametru, jeśli rozmiar buforu jest zbyt mały. Funkcje odczytane z buforów wejściowych, takie jak `gets` , mają bezpieczne wersje, które wymagają określenia maksymalnego rozmiaru.

- `Null termination`. Niektóre funkcje, które nie mogą być niezakończonymi ciągami, mają bezpieczne wersje, co gwarantuje, że ciągi są prawidłowo zakończone wartością null.

- `Enhanced error reporting`. Funkcje Secure zwracają kody błędów z więcej informacji o błędach niż to, które były dostępne w przypadku istniejących funkcji. Funkcje Secure i wiele wcześniej istniejących funkcji teraz ustawiają `errno` i często zwracają `errno` typ kodu, aby zapewnić lepsze raportowanie błędów.

- `Filesystem security`. Bezpieczne interfejsy API we/wy plików obsługują bezpieczny dostęp do plików w domyślnym przypadku.

- `Windows security`. Interfejsy API bezpiecznego przetwarzania wymuszają zasady zabezpieczeń i zezwalają na określenie list kontroli dostępu.

- `Format string syntax checking`. Wykryto nieprawidłowe ciągi, na przykład przy użyciu nieprawidłowych znaków pola typu w `printf` ciągach formatu.

## <a name="see-also"></a>Zobacz też

[Sprawdzanie poprawności parametru](../c-runtime-library/parameter-validation.md)<br/>
[Bezpieczne przeciążenia szablonów](../c-runtime-library/secure-template-overloads.md)<br/>
[Funkcje biblioteki CRT](../c-runtime-library/crt-library-features.md)
