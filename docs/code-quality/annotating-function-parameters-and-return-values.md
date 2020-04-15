---
title: Dodawanie adnotacji do parametrów funkcji i wartości zwracane
description: Przewodnik po parametrach funkcji i adnotacjach wartości zwracanej.
ms.date: 10/15/2019
ms.topic: conceptual
f1_keywords:
- _Outptr_opt_result_bytebuffer_to_
- _Inout_updates_all_opt_
- _Post_equal_to_
- _Outptr_opt_result_maybenull_
- _Out_writes_bytes_all_
- _Out_writes_all_opt_
- _In_opt_
- _Outptr_
- _Outptr_result_maybenull_
- _Outref_result_bytebuffer_all_maybenull_
- _Inout_updates_opt_z_
- _Inout_updates_z_
- _Out_writes_
- _Out_writes_to_ptr_opt_z_
- _In_reads_to_ptr_opt_
- _Ret_writes_to_maybenull_
- _Outref_result_maybenull_
- _Ret_writes_bytes_
- _Outptr_result_bytebuffer_
- _Out_writes_opt_
- _Inout_updates_bytes_opt_
- _In_z_
- _Inout_updates_to_
- _Ret_maybenull_
- _Ret_writes_bytes_to_
- _Ret_z_
- _COM_Outptr_
- _Ret_maybenull_z_
- _Out_opt_
- _In_reads_opt_z_
- _Outptr_result_bytebuffer_to_
- _Ret_notnull_
- _COM_Outptr_opt_result_maybenull_
- _Inout_updates_to_opt_
- _Inout_updates_
- _Outptr_opt_result_buffer_
- _Outptr_result_buffer_to_
- _Out_writes_to_ptr_opt_
- _Out_writes_bytes_all_opt_
- _Inout_updates_all_
- _Deref_inout_range_
- _Ret_writes_
- _Out_writes_z_
- _Ret_writes_to_
- _Out_writes_to_ptr_z_
- _Out_writes_bytes_to_opt_
- _In_reads_or_z_
- _Inout_updates_bytes_to_
- _In_reads_z_
- _In_opt_z_
- _Outref_result_buffer_maybenull_
- _Ret_range_
- _COM_Outptr_opt_
- _Outptr_opt_result_maybenull_z_
- _In_reads_opt_
- _Inout_
- _Field_range_
- _Ret_writes_z_
- _Out_writes_to_
- _Out_writes_to_ptr_
- _Inout_opt_z_
- _Outref_
- _Deref_out_range_
- _Outref_result_buffer_
- _Outref_result_buffer_to_
- _Outref_result_bytebuffer_to_maybenull_
- _In_reads_bytes_
- _Outptr_opt_result_buffer_to_
- _Outref_result_buffer_all_
- _Out_writes_bytes_to_
- _Result_zeroonfailure_
- _In_reads_bytes_opt_
- _Outref_result_buffer_to_maybenull_
- _Outref_result_bytebuffer_all_
- _Outref_result_buffer_all_maybenull_
- _Ret_writes_maybenull_z_
- _In_range_
- _Inout_updates_bytes_all_opt_
- _Outref_result_bytebuffer_to_
- _Inout_updates_bytes_to_opt_
- _Pre_equal_to_
- _Ret_writes_bytes_maybenull_
- _COM_Outptr_result_maybenull_
- _Ret_writes_maybenull_
- _Out_writes_bytes_
- _Outptr_opt_
- _Out_writes_opt_z_
- _Outref_result_nullonfailure_
- _Outptr_opt_result_z_
- _Inout_opt_
- _Deref_in_range_
- _Outptr_result_z_
- _In_reads_to_ptr_opt_z_
- _Struct_size_bytes_
- _Outptr_result_nullonfailure_
- _In_
- _Inout_updates_bytes_
- _In_reads_to_ptr_z_
- _Ret_writes_bytes_to_maybenull
- _Outptr_opt_result_nullonfailure_
- _In_reads_to_ptr_
- _Outptr_result_buffer_
- _Out_
- _Outref_result_bytebuffer_maybenull_
- _Outptr_result_maybenull_z_
- _In_reads_
- _Inout_updates_opt_
- _Out_writes_to_opt_
- _Outptr_opt_result_bytebuffer_
- _Out_writes_all_
- _Out_range_
- _Inout_updates_bytes_all_
- _Inout_z_
- _Outref_result_bytebuffer_
- _Result_nullonfailure_
- _Ret_null_
- _Scanf_format_string_
- _Scanf_s_format_string_
- _Printf_format_string_
ms.assetid: 82826a3d-0c81-421c-8ffe-4072555dca3a
ms.openlocfilehash: c787dcfb252da1abe47251d66c46689db289cf15
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328012"
---
# <a name="annotating-function-parameters-and-return-values"></a>Dodawanie adnotacji do parametrów funkcji i wartości zwracane

W tym artykule opisano typowe zastosowania adnotacji dla prostych parametrów funkcji — skalarnych i wskaźników do struktur i klas — oraz większości rodzajów buforów. W tym artykule przedstawiono również typowe wzorce użycia adnotacji. Aby uzyskać dodatkowe adnotacje związane z funkcjami, zobacz [Zachowanie funkcji adnotacji](../code-quality/annotating-function-behavior.md).

## <a name="pointer-parameters"></a>Parametry wskaźnika

W przypadku adnotacji w poniższej tabeli, gdy parametr wskaźnika jest opisywany, analizator zgłasza błąd, jeśli wskaźnik ma wartość null. Ta adnotacja dotyczy wskaźników i dowolnego elementu danych, który jest wskazyny.

### <a name="annotations-and-descriptions"></a>Adnotacje i opisy

- `_In_`

     Adnotacje parametry wejściowe, które są skalarne, struktury, wskaźniki do struktur i tym podobne. Jawnie mogą być używane na prostych skalarnych. Parametr musi być prawidłowy w stanie wstępnym i nie zostanie zmodyfikowany.

- `_Out_`

     Adnotacje parametry wyjściowe, które są skalarne, struktury, wskaźniki do struktur i tym podobne. Nie należy stosować tej adnotacji do obiektu, który nie może zwrócić wartości — na przykład skalarnej, która jest przekazywana przez wartość. Parametr nie musi być prawidłowy w stanie wstępnym, ale musi być prawidłowy w stanie post-state.

- `_Inout_`

     Adnotacje parametr, który zostanie zmieniony przez funkcję. Musi być prawidłowy zarówno w stanie wstępnym, jak i po stanie, ale zakłada się, że mają różne wartości przed i po wywołaniu. Musi dotyczyć wartości modyfikowalne.

- `_In_z_`

     Wskaźnik do ciągu zakończonego wartością null, który jest używany jako dane wejściowe. Ciąg musi być prawidłowy w stanie wstępnym. Preferowane `PSTR`są warianty , które mają już poprawne adnotacje.

- `_Inout_z_`

     Wskaźnik do tablicy znaków zakończonej wartością null, która zostanie zmodyfikowana. Musi być prawidłowy przed i po wywołaniu, ale zakłada się, że wartość została zmieniona. Terminator null mogą zostać przeniesione, ale tylko elementy do oryginalnego terminatora null mogą być dostępne.

- `_In_reads_(s)`

     `_In_reads_bytes_(s)`

     Wskaźnik do tablicy, który jest odczytywany przez funkcję. Tablica ma `s` rozmiar elementów, z których wszystkie muszą być prawidłowe.

     Wariant `_bytes_` daje rozmiar w bajtach zamiast elementów. Tego wariantu należy używać tylko wtedy, gdy rozmiar nie może być wyrażony jako elementy. Na przykład `char` ciągi będzie `_bytes_` używać wariantu tylko wtedy, gdy podobna funkcja, która używa `wchar_t` będzie.

- `_In_reads_z_(s)`

     Wskaźnik do tablicy, która jest zakończona z wartością null i ma znany rozmiar. Elementy do terminatora zerowego `s` lub jeśli nie ma zerowego terminatora , muszą być prawidłowe w stanie wstępnym. Jeśli rozmiar jest znany w `s` bajtach, skaluj według rozmiaru elementu.

- `_In_reads_or_z_(s)`

     Wskaźnik do tablicy, która jest zakończona z wartością null lub ma znany rozmiar lub oba. Elementy do terminatora zerowego `s` lub jeśli nie ma zerowego terminatora , muszą być prawidłowe w stanie wstępnym. Jeśli rozmiar jest znany w `s` bajtach, skaluj według rozmiaru elementu. (Używane dla `strn` rodziny.)

- `_Out_writes_(s)`

     `_Out_writes_bytes_(s)`

     Wskaźnik do tablicy `s` elementów (resp. bajtów), które zostaną zapisane przez funkcję. Elementy tablicy nie muszą być prawidłowe w stanie wstępnym, a liczba elementów, które są prawidłowe w stanie post-state jest nieokreślony. Jeśli istnieją adnotacje na typ parametru, są one stosowane w stanie post.If there are adnotations on the parameter type, they're applied in post-state. Rozważmy na przykład następujący kod.

     ```cpp
     typedef _Null_terminated_ wchar_t *PWSTR;
     void MyStringCopy(_Out_writes_(size) PWSTR p1, _In_ size_t size, _In_ PWSTR p2);
     ```

     W tym przykładzie wywołujący udostępnia `size` bufor `p1`elementów dla . `MyStringCopy`sprawia, że niektóre z tych elementów są ważne. Co ważniejsze, `_Null_terminated_` adnotacja `PWSTR` na `p1` oznacza, że jest null-zakończone w stanie post.More importantly, the adnotation on means that is null-terminated in post-state. W ten sposób liczba prawidłowych elementów jest nadal dobrze zdefiniowana, ale liczba określonych elementów nie jest wymagana.

     Wariant `_bytes_` daje rozmiar w bajtach zamiast elementów. Tego wariantu należy używać tylko wtedy, gdy rozmiar nie może być wyrażony jako elementy. Na przykład `char` ciągi będzie `_bytes_` używać wariantu tylko wtedy, gdy podobna funkcja, która używa `wchar_t` będzie.

- `_Out_writes_z_(s)`

     Wskaźnik do tablicy `s` elementów. Elementy nie muszą być prawidłowe w stanie wstępnym. W stanie post elementy w górę przez null terminator, który musi być obecny, muszą być prawidłowe. Jeśli rozmiar jest znany w `s` bajtach, skaluj według rozmiaru elementu.

- `_Inout_updates_(s)`

     `_Inout_updates_bytes_(s)`

     Wskaźnik do tablicy, która jest odczytywana i zapisywana w funkcji. Jest to rozmiar `s` elementów i ważne w stanie wstępnym i post-state.

     Wariant `_bytes_` daje rozmiar w bajtach zamiast elementów. Tego wariantu należy używać tylko wtedy, gdy rozmiar nie może być wyrażony jako elementy. Na przykład `char` ciągi będzie `_bytes_` używać wariantu tylko wtedy, gdy podobna funkcja, która używa `wchar_t` będzie.

- `_Inout_updates_z_(s)`

     Wskaźnik do tablicy, która jest zakończona z wartością null i ma znany rozmiar. Elementy w górę przez null terminator, który musi być obecny, muszą być prawidłowe zarówno w stanie wstępnym i post-state. Przyjmuje się, że wartość w stanie post-state różni się od wartości w stanie wstępnym; który obejmuje lokalizację terminatora zerowego. Jeśli rozmiar jest znany w `s` bajtach, skaluj według rozmiaru elementu.

- `_Out_writes_to_(s,c)`

     `_Out_writes_bytes_to_(s,c)`

     `_Out_writes_all_(s)`

     `_Out_writes_bytes_all_(s)`

     Wskaźnik do tablicy `s` elementów. Elementy nie muszą być prawidłowe w stanie wstępnym. W stanie post-state elementy `c`do -th element musi być prawidłowy. Wariant `_bytes_` może służyć, jeśli rozmiar jest znany w bajtach, a nie liczba elementów.

     Przykład:

     ```cpp
     void *memcpy(_Out_writes_bytes_all_(s) char *p1, _In_reads_bytes_(s) char *p2, _In_ int s);
     void *wordcpy(_Out_writes_all_(s) DWORD *p1, _In_reads_(s) DWORD *p2, _In_ int s);
     ```

- `_Inout_updates_to_(s,c)`

     `_Inout_updates_bytes_to_(s,c)`

     Wskaźnik do tablicy, która jest odczytywana i zapisywana przez funkcję. Jest to rozmiar `s` elementów, z których wszystkie muszą być `c` prawidłowe w stanie wstępnym, a elementy muszą być prawidłowe w stanie post-state.

     Wariant `_bytes_` daje rozmiar w bajtach zamiast elementów. Tego wariantu należy używać tylko wtedy, gdy rozmiar nie może być wyrażony jako elementy. Na przykład `char` ciągi będzie `_bytes_` używać wariantu tylko wtedy, gdy podobna funkcja, która używa `wchar_t` będzie.

- `_Inout_updates_all_(s)`

     `_Inout_updates_bytes_all_(s)`

     Wskaźnik do tablicy, która jest odczytywana i `s` zapisywana przez funkcję elementów size. Zdefiniowane jako równoważne:

     `_Inout_updates_to_(_Old_(s), _Old_(s))    _Inout_updates_bytes_to_(_Old_(s), _Old_(s))`

     Innymi słowy każdy element, który istnieje w `s` buforze do w stanie wstępnym jest prawidłowy w stanie wstępnym i post-state.

     Wariant `_bytes_` daje rozmiar w bajtach zamiast elementów. Tego wariantu należy używać tylko wtedy, gdy rozmiar nie może być wyrażony jako elementy. Na przykład `char` ciągi będzie `_bytes_` używać wariantu tylko wtedy, gdy podobna funkcja, która używa `wchar_t` będzie.

- `_In_reads_to_ptr_(p)`

     Wskaźnik do tablicy, `p - _Curr_` `p` dla której `_Curr_`(czyli minus) jest prawidłowym wyrażeniem. Elementy przed `p` musi być prawidłowy w stanie wstępnym.

    Przykład:

    ```cpp
    int ReadAllElements(_In_reads_to_ptr_(EndOfArray) const int *Array, const int *EndOfArray);
    ```

- `_In_reads_to_ptr_z_(p)`

     Wskaźnik do tablicy zakończonej wartością `p - _Curr_` null, `p` dla `_Curr_`której wyrażenie (czyli minus) jest prawidłowym wyrażeniem. Elementy przed `p` musi być prawidłowy w stanie wstępnym.

- `_Out_writes_to_ptr_(p)`

     Wskaźnik do tablicy, `p - _Curr_` `p` dla której `_Curr_`(czyli minus) jest prawidłowym wyrażeniem. Elementy przed `p` nie muszą być prawidłowe w stanie wstępnym i muszą być prawidłowe w stanie post-state.

- `_Out_writes_to_ptr_z_(p)`

     Wskaźnik do tablicy zakończonej wartością `p - _Curr_` null, `p` `_Curr_`dla której (czyli minus) jest prawidłowym wyrażeniem. Elementy przed `p` nie muszą być prawidłowe w stanie wstępnym i muszą być prawidłowe w stanie post-state.

## <a name="optional-pointer-parameters"></a>Opcjonalne parametry wskaźnika

Jeśli zawiera adnotację `_opt_`parametru wskaźnika, oznacza to, że parametr może mieć wartość null. W przeciwnym razie adnotacja zachowuje się tak samo `_opt_`jak wersja, która nie zawiera . Oto lista `_opt_` wariantów adnotacji parametru wskaźnika:

||||
|-|-|-|
|`_In_opt_`<br /><br /> `_Out_opt_`<br /><br /> `_Inout_opt_`<br /><br /> `_In_opt_z_`<br /><br /> `_Inout_opt_z_`<br /><br /> `_In_reads_opt_`<br /><br /> `_In_reads_bytes_opt_`<br /><br /> `_In_reads_opt_z_`|`_Out_writes_opt_`<br /><br /> `_Out_writes_opt_z_`<br /><br /> `_Inout_updates_opt_`<br /><br /> `_Inout_updates_bytes_opt_`<br /><br /> `_Inout_updates_opt_z_`<br /><br /> `_Out_writes_to_opt_`<br /><br /> `_Out_writes_bytes_to_opt_`<br /><br /> `_Out_writes_all_opt_`<br /><br /> `_Out_writes_bytes_all_opt_`|`_Inout_updates_to_opt_`<br /><br /> `_Inout_updates_bytes_to_opt_`<br /><br /> `_Inout_updates_all_opt_`<br /><br /> `_Inout_updates_bytes_all_opt_`<br /><br /> `_In_reads_to_ptr_opt_`<br /><br /> `_In_reads_to_ptr_opt_z_`<br /><br /> `_Out_writes_to_ptr_opt_`<br /><br /> `_Out_writes_to_ptr_opt_z_`|

## <a name="output-pointer-parameters"></a>Parametry wskaźnika wyjściowego

Parametry wskaźnika wyjściowego wymagają specjalnego notacji, aby odróżnić wartość nullness na parametr i lokalizację wskazywaną.

### <a name="annotations-and-descriptions"></a>Adnotacje i opisy

- `_Outptr_`

   Parametr nie może być null, a w stanie post-to lokalizacja nie może być null i musi być prawidłowa.

- `_Outptr_opt_`

   Parametr może mieć wartość null, ale w stanie post lokalizacja wskazała nie może być null i musi być prawidłowa.

- `_Outptr_result_maybenull_`

   Parametr nie może być null, a w stanie post-do lokalizacji wskazał może być null.

- `_Outptr_opt_result_maybenull_`

   Parametr może mieć wartość null, a w stanie post-to lokalizacja może mieć wartość null.

  W poniższej tabeli dodatkowe podciągi są wstawiane do nazwy adnotacji, aby dodatkowo kwalifikować znaczenie adnotacji. Różne podciągi `_z`to `_COM_` `_buffer_`, `_bytebuffer_`, `_to_`, i .

> [!IMPORTANT]
> Jeśli interfejs, który są adnotacjami jest COM, należy użyć formularza COM tych adnotacji. Nie używaj adnotacji COM z interfejsem innego typu.

- `_Outptr_result_z_`

   `_Outptr_opt_result_z_`

   `_Outptr_result_maybenull_z_`

   `_Outptr_opt_result_maybenull_z_`

   Zwrócony wskaźnik `_Null_terminated_` ma adnotację.

- `_COM_Outptr_`

   `_COM_Outptr_opt_`

   `_COM_Outptr_result_maybenull_`

   `_COM_Outptr_opt_result_maybenull_`

   Zwrócony wskaźnik ma semantyki COM i `_On_failure_` dlatego zawiera warunek post-condition, że zwrócony wskaźnik jest null.

- `_Outptr_result_buffer_(s)`

   `_Outptr_result_bytebuffer_(s)`

   `_Outptr_opt_result_buffer_(s)`

   `_Outptr_opt_result_bytebuffer_(s)`

   Zwrócony wskaźnik wskazuje prawidłowy `s` bufor elementów rozmiaru lub bajtów.

- `_Outptr_result_buffer_to_(s, c)`

   `_Outptr_result_bytebuffer_to_(s, c)`

   `_Outptr_opt_result_buffer_to_(s,c)`

   `_Outptr_opt_result_bytebuffer_to_(s,c)`

   Zwrócony wskaźnik wskazuje bufor `s` elementów rozmiaru lub bajtów, z których pierwszy `c` są prawidłowe.

Niektóre konwencje interfejsu zakładają, że parametry wyjściowe są unieważnione w przypadku awarii. Z wyjątkiem jawnie com kod, formularze w poniższej tabeli są preferowane. W przypadku kodu COM należy użyć odpowiednich formularzy COM wymienionych w poprzedniej sekcji.

- `_Result_nullonfailure_`

   Modyfikuje inne adnotacje. Wynik jest ustawiony na wartość null, jeśli funkcja nie powiedzie się.

- `_Result_zeroonfailure_`

   Modyfikuje inne adnotacje. Wynik jest ustawiony na zero, jeśli funkcja nie powiedzie się.

- `_Outptr_result_nullonfailure_`

   Zwrócony wskaźnik wskazuje prawidłowy bufor, jeśli funkcja powiedzie się lub null, jeśli funkcja nie powiedzie się. Ta adnotacja jest dla parametru nieopcjonalne.

- `_Outptr_opt_result_nullonfailure_`

   Zwrócony wskaźnik wskazuje prawidłowy bufor, jeśli funkcja powiedzie się lub null, jeśli funkcja nie powiedzie się. Ta adnotacja jest dla parametru opcjonalnego.

- `_Outref_result_nullonfailure_`

   Zwrócony wskaźnik wskazuje prawidłowy bufor, jeśli funkcja powiedzie się lub null, jeśli funkcja nie powiedzie się. Ta adnotacja jest dla parametru referencyjnego.

## <a name="output-reference-parameters"></a>Parametry odniesienia wyjściowego

Typowym zastosowaniem parametru referencyjnego jest dla parametrów wyjściowych. Dla prostych parametrów `int&`odniesienia `_Out_` wyjścia, takich jak , zapewnia prawidłową semantykę. Jednak gdy wartość wyjściowa jest `int *&`wskaźnikiem, takim jak `_Outptr_ int **` , adnotacje równoważnego wskaźnika, takie jak nie zapewniają poprawnej semantyki. Aby zwięźle wyrazić semantyką parametrów odniesienia wyjściowego dla typów wskaźników, należy użyć tych adnotacji złożonych:

### <a name="annotations-and-descriptions"></a>Adnotacje i opisy

- `_Outref_`

     Wynik musi być prawidłowy w stanie post-state i nie może być null.

- `_Outref_result_maybenull_`

     Wynik musi być prawidłowy w stanie post-state, ale może być null w stanie post-state.

- `_Outref_result_buffer_(s)`

     Wynik musi być prawidłowy w stanie post-state i nie może być null. Wskazuje prawidłowy bufor `s` elementów rozmiaru.

- `_Outref_result_bytebuffer_(s)`

     Wynik musi być prawidłowy w stanie post-state i nie może być null. Wskazuje prawidłowy bufor `s` bajtów rozmiaru.

- `_Outref_result_buffer_to_(s, c)`

     Wynik musi być prawidłowy w stanie post-state i nie może być null. Wskazuje bufor `s` elementów, z `c` których pierwszy jest prawidłowy.

- `_Outref_result_bytebuffer_to_(s, c)`

     Wynik musi być prawidłowy w stanie post-state i nie może być null. Wskazuje bufor `s` bajtów, z `c` których pierwszy jest prawidłowy.

- `_Outref_result_buffer_all_(s)`

     Wynik musi być prawidłowy w stanie post-state i nie może być null. Wskazuje prawidłowy bufor `s` elementów prawidłowych rozmiarów.

- `_Outref_result_bytebuffer_all_(s)`

     Wynik musi być prawidłowy w stanie post-state i nie może być null. Wskazuje prawidłowy `s` bufor bajtów prawidłowych elementów.

- `_Outref_result_buffer_maybenull_(s)`

     Wynik musi być prawidłowy w stanie post-state, ale może być null w stanie post-state. Wskazuje prawidłowy bufor `s` elementów rozmiaru.

- `_Outref_result_bytebuffer_maybenull_(s)`

     Wynik musi być prawidłowy w stanie post-state, ale może być null w stanie post-state. Wskazuje prawidłowy bufor `s` bajtów rozmiaru.

- `_Outref_result_buffer_to_maybenull_(s, c)`

     Wynik musi być prawidłowy w stanie post-state, ale może być null w stanie post-state. Wskazuje bufor `s` elementów, z `c` których pierwszy jest prawidłowy.

- `_Outref_result_bytebuffer_to_maybenull_(s,c)`

     Wynik musi być prawidłowy w stanie post,ale może być null w stanie post. Wskazuje bufor `s` bajtów, z `c` których pierwszy jest prawidłowy.

- `_Outref_result_buffer_all_maybenull_(s)`

     Wynik musi być prawidłowy w stanie post,ale może być null w stanie post. Wskazuje prawidłowy bufor `s` elementów prawidłowych rozmiarów.

- `_Outref_result_bytebuffer_all_maybenull_(s)`

     Wynik musi być prawidłowy w stanie post,ale może być null w stanie post. Wskazuje prawidłowy `s` bufor bajtów prawidłowych elementów.

## <a name="return-values"></a>Zwracane wartości

Zwracana wartość funkcji przypomina `_Out_` parametr, ale jest na innym poziomie de-reference i nie trzeba brać pod uwagę pojęcia wskaźnika do wyniku. W przypadku następujących adnotacji wartością zwracaną jest obiekt z adnotacjami — skalar, wskaźnik do struktury lub wskaźnik do buforu. Adnotacje te mają taką samą semantyką jak odpowiednia `_Out_` adnotacja.

|||
|-|-|
|`_Ret_z_`<br /><br /> `_Ret_writes_(s)`<br /><br /> `_Ret_writes_bytes_(s)`<br /><br /> `_Ret_writes_z_(s)`<br /><br /> `_Ret_writes_to_(s,c)`<br /><br /> `_Ret_writes_maybenull_(s)`<br /><br /> `_Ret_writes_to_maybenull_(s)`<br /><br /> `_Ret_writes_maybenull_z_(s)`|`_Ret_maybenull_`<br /><br /> `_Ret_maybenull_z_`<br /><br /> `_Ret_null_`<br /><br /> `_Ret_notnull_`<br /><br /> `_Ret_writes_bytes_to_`<br /><br /> `_Ret_writes_bytes_maybenull_`<br /><br /> `_Ret_writes_bytes_to_maybenull_`|

## <a name="format-string-parameters"></a>Formatowanie parametrów ciągu

- `_Printf_format_string_`Wskazuje, że parametr jest ciągiem formatu do użycia w wyrażeniu. `printf`

     **Przykład**

    ```cpp
    int MyPrintF(_Printf_format_string_ const wchar_t* format, ...)
    {
           va_list args;
           va_start(args, format);
           int ret = vwprintf(format, args);
           va_end(args);
           return ret;
    }
    ```

- `_Scanf_format_string_`Wskazuje, że parametr jest ciągiem formatu do użycia w wyrażeniu. `scanf`

     **Przykład**

    ```cpp
    int MyScanF(_Scanf_format_string_ const wchar_t* format, ...)
    {
           va_list args;
           va_start(args, format);
           int ret = vwscanf(format, args);
           va_end(args);
           return ret;
    }
    ```

- `_Scanf_s_format_string_`Wskazuje, że parametr jest ciągiem formatu do użycia w wyrażeniu. `scanf_s`

     **Przykład**

    ```cpp
    int MyScanF_s(_Scanf_s_format_string_ const wchar_t* format, ...)
    {
           va_list args;
           va_start(args, format);
           int ret = vwscanf_s(format, args);
           va_end(args);
           return ret;
    }
    ```

## <a name="other-common-annotations"></a>Inne popularne adnotacje

### <a name="annotations-and-descriptions"></a>Adnotacje i opisy

- `_In_range_(low, hi)`

     `_Out_range_(low, hi)`

     `_Ret_range_(low, hi)`

     `_Deref_in_range_(low, hi)`

     `_Deref_out_range_(low, hi)`

     `_Deref_inout_range_(low, hi)`

     `_Field_range_(low, hi)`

     Parametr, pole lub wynik znajduje się w `low` zakresie `hi`(włącznie) od do . Równoważne `_Satisfies_(_Curr_ >= low && _Curr_ <= hi)` z tym jest stosowany do obiektu z adnotacjami wraz z odpowiednimi warunkami pre-state lub post-state.

    > [!IMPORTANT]
    > Chociaż nazwy zawierają "in" i "out", semantyka `_In_` i `_Out_` **nie** mają zastosowania do tych adnotacji.

- `_Pre_equal_to_(expr)`

     `_Post_equal_to_(expr)`

     Wartość z adnotacjami `expr`jest dokładnie . Równoważne `_Satisfies_(_Curr_ == expr)` z tym jest stosowany do obiektu z adnotacjami wraz z odpowiednimi warunkami pre-state lub post-state.

- `_Struct_size_bytes_(size)`

     Dotyczy deklaracji struktury lub klasy. Wskazuje, że prawidłowy obiekt tego typu może być większy niż zadeklarowany typ, przy czym liczba bajtów jest podana przez `size`program . Przykład:

     `typedef _Struct_size_bytes_(nSize) struct MyStruct {    size_t nSize;    ... };`

     Rozmiar buforu w bajtach `pM` `MyStruct *` parametru typu jest następnie brany za:

     `min(pM->nSize, sizeof(MyStruct))`

## <a name="related-resources"></a>Powiązane zasoby

[Blog zespołu analizy kodu](https://blogs.msdn.microsoft.com/codeanalysis/)

## <a name="see-also"></a>Zobacz też

- [Korzystanie z adnotacji SAL w celu zmniejszenia liczby defektów kodu C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)
- [Poznanie SAL](../code-quality/understanding-sal.md)
- [Zachowanie funkcji dodawania adnotacji](../code-quality/annotating-function-behavior.md)
- [Dodawanie adnotacji struktur i klas](../code-quality/annotating-structs-and-classes.md)
- [Dodawanie adnotacji do zachowania blokującego](../code-quality/annotating-locking-behavior.md)
- [Określanie miejsca i warunków stosowania adnotacji](../code-quality/specifying-when-and-where-an-annotation-applies.md)
- [Funkcje wewnętrzne](../code-quality/intrinsic-functions.md)
- [Najlepsze rozwiązania i przykłady](../code-quality/best-practices-and-examples-sal.md)
