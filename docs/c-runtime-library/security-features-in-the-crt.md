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
ms.openlocfilehash: a6ebbb09bc724fe1d3b2f06a27cb6708acb7566b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50538363"
---
# <a name="security-features-in-the-crt"></a>Funkcje zabezpieczeń w CRT

Wiele funkcji CRT stare ma nowsze, bezpieczniejsze wersje. Jeśli istnieje funkcja bezpieczny, starsze, mniej bezpieczna opcja wersji zostanie oznaczony jako przestarzały i nowa wersja ma `_s` sufiks ("bezpieczne").

W tym kontekście "przestarzałe" po prostu oznacza, że funkcja nie jest zalecane; nie oznacza to, że funkcja jest zaplanowane do usunięcia z CRT.

Bezpieczne funkcje nie jest w stanie zapobiec ani poprawianie błędów zabezpieczeń; zamiast ich wychwytywanie błędów, kiedy się pojawią. Wykonują dodatkowe czynności kontrolne dla warunków błędu, a w przypadku błędu, wywołują procedurę obsługi błędów (zobacz [Parameter Validation](../c-runtime-library/parameter-validation.md)).

Na przykład `strcpy` funkcji nie ma możliwości informuje, jeśli ciąg, który kopiuje on są za duże dla buforu docelowego. Jednak jego odpowiednika bezpieczny, `strcpy_s`, pobiera rozmiar buforu jako parametr, dzięki czemu można określić, jeśli przepełnienie buforu zostanie przeprowadzona. Jeśli używasz `strcpy_s` można skopiować jedenaście znaków do bufora dziesięć znaków, który błędu ze strony użytkownika; `strcpy_s` nie można poprawić swoje pomyłkę, ale można wykryć błędu i poinformuje, wywołując program obsługi nieprawidłowych parametrów.

## <a name="eliminating-deprecation-warnings"></a>Wyeliminowanie ostrzeżeń dotyczących zakończenia obsługi

Istnieje kilka sposobów, aby wyeliminować ostrzeżeń dotyczących zakończenia obsługi dla starsze, mniej bezpieczne funkcje. Najprostszą jest po prostu określenie `_CRT_SECURE_NO_WARNINGS` lub użyj [ostrzeżenie](../preprocessor/warning.md) pragmy. To spowoduje wyłączenie ostrzeżeń dotyczących zakończenia obsługi, ale oczywiście nadal istnieją problemy z zabezpieczeniami, które spowodowały ostrzeżenia. Jest to znacznie lepiej pozostawić wycofywania ostrzeżenia włączone i korzystać z zalet nowych funkcji zabezpieczeń w CRT.

W języku C++, najprostszym sposobem wykonania tego zadania jest użycie [przeciążenia bezpiecznych szablonów](../c-runtime-library/secure-template-overloads.md), który w wielu przypadkach zostanie całkowicie wyeliminować ostrzeżeń dotyczących zakończenia obsługi, zastępując wywołania funkcji przestarzałe wywołania do nowego bezpieczne wersje tych funkcji. Na przykład, należy wziąć pod uwagę to przestarzała wywołanie `strcpy`:

```
char szBuf[10];
strcpy(szBuf, "test"); // warning: deprecated
```

Definiowanie `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` jako 1 eliminuje to ostrzeżenie, zmieniając `strcpy` wywołanie `strcpy_s`, co uniemożliwia przepełnienia buforu. Aby uzyskać więcej informacji, zobacz [Secure przeciążenia szablonu](../c-runtime-library/secure-template-overloads.md).

W przypadku tych przestarzałych funkcji bez przeciążenia bezpiecznych szablonów zdecydowanie rozważ ręczne aktualizowanie kodu, aby użyć bezpieczne wersje.

Innym źródłem ostrzeżeń dotyczących zakończenia obsługi niezwiązanych z zabezpieczeniami, to funkcje POSIX. Zamień nazwy funkcji POSIX ich odpowiedników standard (na przykład zmienić [dostępu](../c-runtime-library/reference/access-crt.md) do [_access](../c-runtime-library/reference/access-waccess.md)), lub wyłącz ostrzeżenia związane z modelem POSIX wycofywania, definiując `_CRT_NONSTDC_NO_WARNINGS`. Aby uzyskać więcej informacji, zobacz [zgodności](compatibility.md).

## <a name="additional-security-features"></a>Dodatkowe funkcje zabezpieczeń

Niektóre funkcje zabezpieczeń obejmują następujące czynności:

- `Parameter Validation`. Parametry przekazane do funkcji CRT są weryfikowane w obu tych funkcji bezpiecznego i wiele wersji istniejących funkcji. Walidacji te obejmują:

   - Sprawdzanie **NULL** wartości przekazywane do funkcji.

   - Sprawdzanie, czy wartości wyliczane ważności.

   - Sprawdzanie, czy w prawidłowe zakresy wartości całkowitych.

- Aby uzyskać więcej informacji, zobacz [Parameter Validation](../c-runtime-library/parameter-validation.md).

- Program obsługi nieprawidłowych parametrów jest również dostępna dla deweloperów. Gdy wystąpią nieprawidłowy parametr, zamiast potwierdzające i zakończeniem działania aplikacji, CRT zapewnia sposób sprawdzić te problemy z [_set_invalid_parameter_handler —, _set_thread_local_invalid_parameter_handler](../c-runtime-library/reference/set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md)funkcji.

- `Sized Buffers`. Bezpieczne funkcje wymagają, że rozmiar buforu można przekazać do żadnej funkcji, która zapisuje do buforu. Bezpieczne wersje sprawdzić, czy bufor jest wystarczająco duży, przed zapisem, pomagając w celu uniknięcia błędów przepełnienia buforu niebezpieczne, umożliwiające wykonywanie złośliwego kodu. Funkcje te zwykle zwracają `errno` typ kodu błędu, a następnie wywołaj procedurę obsługi nieprawidłowego parametru, jeśli rozmiar buforu jest za mały. Funkcje, które odczytują z bufory wejściowe, takie jak `gets`, ma bezpieczne wersje, które wymagają określenia maksymalnego rozmiaru.

- `Null termination`. Niektóre funkcje, które pozostawione ciągi potencjalnie bez zakończone mają bezpieczne wersje, które upewnij się, że ciągi są prawidłowo zakończony znakiem null.

- `Enhanced error reporting`. Bezpieczne funkcje zwracają kodów błędów z dodatkowymi informacjami błędów, niż było dostępne z istniejących funkcji. Bezpieczne funkcje i wiele z istniejących funkcji teraz ustawić `errno` i często zwracają `errno` kodu typu, aby zapewnić lepsze raportowanie błędów.

- `Filesystem security`. Plik bezpieczny dostęp do bezpiecznych plików pomocy technicznej interfejsów API we/wy w przypadku domyślnej.

- `Windows security`. Proces bezpieczne interfejsy API wymuszać zasady zabezpieczeń i umożliwiają listy ACL, aby określić.

- `Format string syntax checking`. Nieprawidłowe ciągi są wykrywane, na przykład przy użyciu znaków nieprawidłowy typ pola `printf` ciągi formatujące.

## <a name="see-also"></a>Zobacz też

[Walidacja parametru](../c-runtime-library/parameter-validation.md)<br/>
[Przeciążenia bezpiecznych szablonów](../c-runtime-library/secure-template-overloads.md)<br/>
[Biblioteka CRT, funkcje](../c-runtime-library/crt-library-features.md)