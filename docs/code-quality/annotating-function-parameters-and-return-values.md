---
title: Dodawanie adnotacji do parametrów funkcji i zwracanych wartości
description: Przewodnik referencyjny do parametrów funkcji i zwracanych wartości.
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
ms.openlocfilehash: d2aa57abc6c0bcc50bcae743a50f86e5de65ab64
ms.sourcegitcommit: 6b3d793f0ef3bbb7eefaf9f372ba570fdfe61199
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/15/2020
ms.locfileid: "86404040"
---
# <a name="annotating-function-parameters-and-return-values"></a>Dodawanie adnotacji do parametrów funkcji i zwracanych wartości

W tym artykule opisano typowe zastosowania adnotacji dla prostych parametrów funkcji — skalarnych i wskaźników do struktur i klas — i większości rodzajów buforów. W tym artykule przedstawiono również typowe wzorce użycia dla adnotacji. Aby uzyskać dodatkowe adnotacje dotyczące funkcji, zobacz [Dodawanie adnotacji do zachowania funkcji](../code-quality/annotating-function-behavior.md).

## <a name="pointer-parameters"></a>Parametry wskaźnika

W przypadku adnotacji w poniższej tabeli, gdy wskaźnik jest oznaczony adnotacją, Analizator zgłosi błąd, jeśli wskaYnik ma wartość null. Ta adnotacja ma zastosowanie do wskaźników i do dowolnego elementu danych, który jest wskazywany przez.

### <a name="annotations-and-descriptions"></a>Adnotacje i opisy

- `_In_`

     Adnotuj parametry wejściowe, które są skalarne, struktury, wskaźniki do struktur i podobne. Jawnie może być używany w prostych wartościach skalarnych. Parametr musi być prawidłowy w stanie sprzed i nie będzie modyfikowany.

- `_Out_`

     Umożliwia dodawanie adnotacji do parametrów wyjściowych, które są skalarne, struktury, wskaźniki do struktur i podobne. Nie stosuj tej adnotacji do obiektu, który nie może zwracać wartości — na przykład wartość skalarna, która jest przenoszona przez wartość. Parametr nie musi być prawidłowy w stanie wstępnym, ale powinien być prawidłowy w stanie post-State.

- `_Inout_`

     Adnotuj parametr, który zostanie zmieniony przez funkcję. Musi być prawidłowy zarówno w stanie sprzed, jak i w stanie, ale zakłada się, że mają różne wartości przed i po wywołaniu. Należy zastosować do modyfikowalnej wartości.

- `_In_z_`

     Wskaźnik do ciągu zakończonego wartością null, który jest używany jako dane wejściowe. Ciąg musi być prawidłowy w stanie sprzed. `PSTR`Preferowane są warianty, które mają już poprawne adnotacje.

- `_Inout_z_`

     Wskaźnik do tablicy znaków zakończonych znakiem null, który zostanie zmodyfikowany. Musi być prawidłowy przed i po wywołaniu, ale zakłada się, że wartość została zmieniona. Terminator o wartości null można przenieść, ale można uzyskać dostęp tylko do elementów do oryginalnego terminatora o wartości null.

- `_In_reads_(s)`

     `_In_reads_bytes_(s)`

     Wskaźnik do tablicy, który jest odczytywany przez funkcję. Tablica zawiera elementy o rozmiarze `s` , które muszą być prawidłowe.

     `_bytes_`Wariant zawiera rozmiar w bajtach, a nie elementy. Tego wariantu należy używać tylko wtedy, gdy rozmiar nie może być wyrażony jako elementy. Na przykład `char` ciągi używają `_bytes_` wariantu tylko wtedy, gdy Podobna funkcja, która używa tej funkcji `wchar_t` .

- `_In_reads_z_(s)`

     Wskaźnik do tablicy, która jest zakończona zerem i ma znany rozmiar. Elementy do terminatora o wartości null lub `s` Jeśli nie ma terminatora o wartości null — muszą być prawidłowe w stanie sprzed. Jeśli rozmiar jest znany w bajtach, Skaluj `s` według rozmiaru elementu.

- `_In_reads_or_z_(s)`

     Wskaźnik do tablicy, która jest zakończona wartością null lub ma znany rozmiar lub oba te elementy. Elementy do terminatora o wartości null lub `s` Jeśli nie ma terminatora o wartości null — muszą być prawidłowe w stanie sprzed. Jeśli rozmiar jest znany w bajtach, Skaluj `s` według rozmiaru elementu. (Używany przez `strn` rodzinę).

- `_Out_writes_(s)`

     `_Out_writes_bytes_(s)`

     Wskaźnik do tablicy `s` elementów (centr. Bytes), który zostanie zapisany przez funkcję. Elementy tablicy nie muszą być prawidłowe w stanie wstępnym, a liczba elementów, które są prawidłowe w stanie post, jest nieokreślona. Jeśli istnieją adnotacje w typie parametru, są one stosowane w stanie post-State. Rozważmy na przykład poniższy kod.

     ```cpp
     typedef _Null_terminated_ wchar_t *PWSTR;
     void MyStringCopy(_Out_writes_(size) PWSTR p1, _In_ size_t size, _In_ PWSTR p2);
     ```

     W tym przykładzie obiekt wywołujący udostępnia bufor `size` elementów dla `p1` . `MyStringCopy`sprawia, że niektóre z tych elementów są prawidłowe. Co ważniejsze, `_Null_terminated_` Adnotacja na `PWSTR` oznacza, że `p1` jest zakończona wartością null w stanie post. W ten sposób liczba prawidłowych elementów jest nadal zdefiniowana, ale określona liczba elementów nie jest wymagana.

     `_bytes_`Wariant zawiera rozmiar w bajtach, a nie elementy. Tego wariantu należy używać tylko wtedy, gdy rozmiar nie może być wyrażony jako elementy. Na przykład `char` ciągi używają `_bytes_` wariantu tylko wtedy, gdy Podobna funkcja, która używa tej funkcji `wchar_t` .

- `_Out_writes_z_(s)`

     Wskaźnik do tablicy `s` elementów. Elementy nie muszą być prawidłowe w stanie sprzed. W Stanach końcowych elementy przez terminator wartości null, które muszą być obecne — muszą być prawidłowe. Jeśli rozmiar jest znany w bajtach, Skaluj `s` według rozmiaru elementu.

- `_Inout_updates_(s)`

     `_Inout_updates_bytes_(s)`

     Wskaźnik do tablicy, który jest odczytywany i zapisywana w funkcji. Jest to rozmiar `s` elementów i jest prawidłowy w stanie sprzed i po nim.

     `_bytes_`Wariant zawiera rozmiar w bajtach, a nie elementy. Tego wariantu należy używać tylko wtedy, gdy rozmiar nie może być wyrażony jako elementy. Na przykład `char` ciągi używają `_bytes_` wariantu tylko wtedy, gdy Podobna funkcja, która używa tej funkcji `wchar_t` .

- `_Inout_updates_z_(s)`

     Wskaźnik do tablicy, która jest zakończona zerem i ma znany rozmiar. Elementy w górę przez terminator o wartości null — które muszą być obecne — muszą być prawidłowe w stanie sprzed i po nim. Wartość w stanie post jest zapuszczalna jako inna niż wartość w stanie sprzed; zawiera lokalizację terminatora o wartości null. Jeśli rozmiar jest znany w bajtach, Skaluj `s` według rozmiaru elementu.

- `_Out_writes_to_(s,c)`

     `_Out_writes_bytes_to_(s,c)`

     `_Out_writes_all_(s)`

     `_Out_writes_bytes_all_(s)`

     Wskaźnik do tablicy `s` elementów. Elementy nie muszą być prawidłowe w stanie sprzed. W stanie post elementy do `c` -th muszą być prawidłowe. `_bytes_`Wariantu można użyć, jeśli rozmiar jest znany w bajtach, a nie na liczbie elementów.

     Na przykład:

     ```cpp
     void *memcpy(_Out_writes_bytes_all_(s) char *p1, _In_reads_bytes_(s) char *p2, _In_ int s);
     void *wordcpy(_Out_writes_all_(s) DWORD *p1, _In_reads_(s) DWORD *p2, _In_ int s);
     ```

- `_Inout_updates_to_(s,c)`

     `_Inout_updates_bytes_to_(s,c)`

     Wskaźnik do tablicy, który jest odczytywany i zapisywana przez funkcję. Jest to element size `s` , który musi być prawidłowy w stanie sprzed i `c` elementy muszą być prawidłowe w stanie post.

     `_bytes_`Wariant zawiera rozmiar w bajtach, a nie elementy. Tego wariantu należy używać tylko wtedy, gdy rozmiar nie może być wyrażony jako elementy. Na przykład `char` ciągi używają `_bytes_` wariantu tylko wtedy, gdy Podobna funkcja, która używa tej funkcji `wchar_t` .

- `_Inout_updates_all_(s)`

     `_Inout_updates_bytes_all_(s)`

     Wskaźnik do tablicy, który jest odczytywany i zapisywana przez funkcję `s` elementów size. Zdefiniowane jako równoważne:

     `_Inout_updates_to_(_Old_(s), _Old_(s))    _Inout_updates_bytes_to_(_Old_(s), _Old_(s))`

     Innymi słowy, każdy element, który istnieje w buforze do `s` w stanie wstępnym, jest prawidłowy w stanie sprzed i po nim.

     `_bytes_`Wariant zawiera rozmiar w bajtach, a nie elementy. Tego wariantu należy używać tylko wtedy, gdy rozmiar nie może być wyrażony jako elementy. Na przykład `char` ciągi używają `_bytes_` wariantu tylko wtedy, gdy Podobna funkcja, która używa tej funkcji `wchar_t` .

- `_In_reads_to_ptr_(p)`

     Wskaźnik do tablicy, dla której `p - _Curr_` (czyli `p` minus `_Curr_` ) jest prawidłowym wyrażeniem. Elementy przed `p` muszą być prawidłowe w stanie sprzed.

    Na przykład:

    ```cpp
    int ReadAllElements(_In_reads_to_ptr_(EndOfArray) const int *Array, const int *EndOfArray);
    ```

- `_In_reads_to_ptr_z_(p)`

     Wskaźnik do tablicy zakończonych znakiem null, dla którego wyrażenie `p - _Curr_` (czyli `p` minus `_Curr_` ) jest prawidłowym wyrażeniem. Elementy przed `p` muszą być prawidłowe w stanie sprzed.

- `_Out_writes_to_ptr_(p)`

     Wskaźnik do tablicy, dla której `p - _Curr_` (czyli `p` minus `_Curr_` ) jest prawidłowym wyrażeniem. Elementy przed `p` nie muszą być prawidłowe w stanie sprzed i muszą być prawidłowe w stanie post.

- `_Out_writes_to_ptr_z_(p)`

     Wskaźnik do tablicy zakończonych znakiem null, dla którego `p - _Curr_` (czyli `p` minus `_Curr_` ) jest prawidłowym wyrażeniem. Elementy przed `p` nie muszą być prawidłowe w stanie sprzed i muszą być prawidłowe w stanie post.

## <a name="optional-pointer-parameters"></a>Opcjonalne parametry wskaźnika

Gdy adnotacja parametru wskaźnika zawiera `_opt_` , wskazuje, że parametr może mieć wartość null. W przeciwnym razie adnotacja zachowuje się tak samo, jak wersja, która nie zawiera `_opt_` . Poniżej znajduje się lista `_opt_` wariantów adnotacji parametrów wskaźnika:

:::row:::
    :::column:::
        `_In_opt_`<br /><br /> `_Out_opt_`<br /><br /> `_Inout_opt_`<br /><br /> `_In_opt_z_`<br /><br /> `_Inout_opt_z_`<br /><br /> `_In_reads_opt_`<br /><br /> `_In_reads_bytes_opt_`<br /><br /> `_In_reads_opt_z_`
    :::column-end:::
    :::column:::
        `_Out_writes_opt_`<br /><br /> `_Out_writes_opt_z_`<br /><br /> `_Inout_updates_opt_`<br /><br /> `_Inout_updates_bytes_opt_`<br /><br /> `_Inout_updates_opt_z_`<br /><br /> `_Out_writes_to_opt_`<br /><br /> `_Out_writes_bytes_to_opt_`<br /><br /> `_Out_writes_all_opt_`<br /><br /> `_Out_writes_bytes_all_opt_`
    :::column-end:::
    :::column:::
        `_Inout_updates_to_opt_`<br /><br /> `_Inout_updates_bytes_to_opt_`<br /><br /> `_Inout_updates_all_opt_`<br /><br /> `_Inout_updates_bytes_all_opt_`<br /><br /> `_In_reads_to_ptr_opt_`<br /><br /> `_In_reads_to_ptr_opt_z_`<br /><br /> `_Out_writes_to_ptr_opt_`<br /><br /> `_Out_writes_to_ptr_opt_z_`
    :::column-end:::
:::row-end:::

## <a name="output-pointer-parameters"></a>Parametry wskaźnika wyjściowego

Parametry wskaźnika danych wyjściowych wymagają specjalnej notacji, aby odróżnić wartości null dla parametru i lokalizacji wskazywanej.

### <a name="annotations-and-descriptions"></a>Adnotacje i opisy

- `_Outptr_`

   Parametr nie może mieć wartości null, a w stanie wskazywanym przez wpis nie może mieć wartości null i musi być prawidłowy.

- `_Outptr_opt_`

   Parametr może mieć wartość null, ale w stanie post wskazuje, że lokalizacja wskazywana nie może mieć wartości null i musi być prawidłowa.

- `_Outptr_result_maybenull_`

   Parametr nie może mieć wartości null, a w stanie wskazywanym przez wartość null.

- `_Outptr_opt_result_maybenull_`

   Parametr może mieć wartość null, a w stanie wskazywanym przez wpis wartość null.

  W poniższej tabeli dodatkowe podciągi są wstawiane do nazwy adnotacji, aby dodatkowo zakwalifikować znaczenie adnotacji. Różne podciągi to `_z` , `_COM_` , `_buffer_` , `_bytebuffer_` i `_to_` .

> [!IMPORTANT]
> Jeśli dodajesz Dodawanie adnotacji do interfejsu COM, użyj formularza COM tych adnotacji. Nie używaj adnotacji COM z żadnym innym interfejsem typu.

- `_Outptr_result_z_`

   `_Outptr_opt_result_z_`

   `_Outptr_result_maybenull_z_`

   `_Outptr_opt_result_maybenull_z_`

   Zwrócony wskaźnik ma `_Null_terminated_` adnotację.

- `_COM_Outptr_`

   `_COM_Outptr_opt_`

   `_COM_Outptr_result_maybenull_`

   `_COM_Outptr_opt_result_maybenull_`

   Zwrócony wskaźnik ma semantykę modelu COM, co oznacza, że jest on przeszukiwany jako `_On_failure_` warunek końcowy, który zwrócony wskaźnik ma wartość null.

- `_Outptr_result_buffer_(s)`

   `_Outptr_result_bytebuffer_(s)`

   `_Outptr_opt_result_buffer_(s)`

   `_Outptr_opt_result_bytebuffer_(s)`

   Zwrócony wskaźnik wskazuje prawidłowy bufor `s` elementów rozmiaru lub bajtów.

- `_Outptr_result_buffer_to_(s, c)`

   `_Outptr_result_bytebuffer_to_(s, c)`

   `_Outptr_opt_result_buffer_to_(s,c)`

   `_Outptr_opt_result_bytebuffer_to_(s,c)`

   Zwrócony wskaźnik wskazuje na bufor `s` elementów rozmiaru lub bajtów, z których pierwszy `c` jest prawidłowy.

Niektóre konwencje interfejsu zakładają, że parametry wyjściowe są nullified w przypadku niepowodzenia. W przypadku jawnego kodu COM formularze w poniższej tabeli są preferowane. W przypadku kodu COM Użyj odpowiednich formularzy COM, które są wymienione w poprzedniej sekcji.

- `_Result_nullonfailure_`

   Modyfikuje inne adnotacje. Jeśli funkcja nie powiedzie się, wynik zostanie ustawiony na wartość null.

- `_Result_zeroonfailure_`

   Modyfikuje inne adnotacje. Jeśli funkcja nie powiedzie się, wynik zostanie ustawiony na zero.

- `_Outptr_result_nullonfailure_`

   Zwrócony wskaźnik wskazuje prawidłowy bufor, jeśli funkcja się powiedzie, lub wartość null, jeśli funkcja się nie powiedzie. Adnotacja jest dla nieopcjonalnego parametru.

- `_Outptr_opt_result_nullonfailure_`

   Zwrócony wskaźnik wskazuje prawidłowy bufor, jeśli funkcja się powiedzie, lub wartość null, jeśli funkcja się nie powiedzie. Ta adnotacja jest dla opcjonalnego parametru.

- `_Outref_result_nullonfailure_`

   Zwrócony wskaźnik wskazuje prawidłowy bufor, jeśli funkcja się powiedzie, lub wartość null, jeśli funkcja się nie powiedzie. Ta adnotacja dotyczy parametru Reference.

## <a name="output-reference-parameters"></a>Parametry odwołania wyjściowego

Typowym zastosowaniem parametru reference jest dla parametrów wyjściowych. W przypadku prostych parametrów referencyjnych, takich jak `int&` , `_Out_` zapewnia poprawną semantykę. Jednakże gdy wartość wyjściowa jest wskaźnikiem, takim jak `int *&` , równoważne adnotacje wskaźnika, takie jak `_Outptr_ int **` nie zapewniają właściwej semantyki. Aby zwięzłie przedstawić semantykę parametrów referencyjnych wyjściowych dla typów wskaźnika, użyj następujących adnotacji złożonych:

### <a name="annotations-and-descriptions"></a>Adnotacje i opisy

- `_Outref_`

     Wynik musi być prawidłowy w stanie post i nie może mieć wartości null.

- `_Outref_result_maybenull_`

     Wynik musi być prawidłowy w stanie post, ale może mieć wartość null w stanie post.

- `_Outref_result_buffer_(s)`

     Wynik musi być prawidłowy w stanie post i nie może mieć wartości null. Wskazuje prawidłowy bufor `s` elementów size.

- `_Outref_result_bytebuffer_(s)`

     Wynik musi być prawidłowy w stanie post i nie może mieć wartości null. Wskazuje prawidłowy bufor wielkości `s` bajtów.

- `_Outref_result_buffer_to_(s, c)`

     Wynik musi być prawidłowy w stanie post i nie może mieć wartości null. Wskazuje bufor `s` elementów, z których pierwszy `c` jest prawidłowy.

- `_Outref_result_bytebuffer_to_(s, c)`

     Wynik musi być prawidłowy w stanie post i nie może mieć wartości null. Wskazuje bufor bajtów, `s` z których pierwszy `c` jest prawidłowy.

- `_Outref_result_buffer_all_(s)`

     Wynik musi być prawidłowy w stanie post i nie może mieć wartości null. Wskazuje prawidłowy bufor `s` prawidłowych elementów.

- `_Outref_result_bytebuffer_all_(s)`

     Wynik musi być prawidłowy w stanie post i nie może mieć wartości null. Wskazuje prawidłowy bufor `s` bajtów prawidłowych elementów.

- `_Outref_result_buffer_maybenull_(s)`

     Wynik musi być prawidłowy w stanie post, ale może mieć wartość null w stanie post. Wskazuje prawidłowy bufor `s` elementów size.

- `_Outref_result_bytebuffer_maybenull_(s)`

     Wynik musi być prawidłowy w stanie post, ale może mieć wartość null w stanie post. Wskazuje prawidłowy bufor wielkości `s` bajtów.

- `_Outref_result_buffer_to_maybenull_(s, c)`

     Wynik musi być prawidłowy w stanie post, ale może mieć wartość null w stanie post. Wskazuje bufor `s` elementów, z których pierwszy `c` jest prawidłowy.

- `_Outref_result_bytebuffer_to_maybenull_(s,c)`

     Wynik musi być prawidłowy w stanie post, ale może mieć wartość null w stanie post. Wskazuje bufor bajtów, `s` z których pierwszy `c` jest prawidłowy.

- `_Outref_result_buffer_all_maybenull_(s)`

     Wynik musi być prawidłowy w stanie post, ale może mieć wartość null w stanie post. Wskazuje prawidłowy bufor `s` prawidłowych elementów.

- `_Outref_result_bytebuffer_all_maybenull_(s)`

     Wynik musi być prawidłowy w stanie post, ale może mieć wartość null w stanie post. Wskazuje prawidłowy bufor `s` bajtów prawidłowych elementów.

## <a name="return-values"></a>Wartości zwracane

Wartość zwracana przez funkcję jest podobna do `_Out_` parametru, ale jest na innym poziomie odwołującym się i nie trzeba traktować koncepcji wskaźnika do wyniku. Dla następujących adnotacji wartość zwracana jest obiektem z adnotacjami — skalarnym, wskaźnikiem do struktury lub wskaźnikiem do buforu. Te adnotacje mają taką samą semantykę, jak odpowiednia `_Out_` adnotacja.

:::row:::
    :::column:::
        `_Ret_z_`<br /><br /> `_Ret_writes_(s)`<br /><br /> `_Ret_writes_bytes_(s)`<br /><br /> `_Ret_writes_z_(s)`<br /><br /> `_Ret_writes_to_(s,c)`<br /><br /> `_Ret_writes_maybenull_(s)`<br /><br /> `_Ret_writes_to_maybenull_(s)`<br /><br /> `_Ret_writes_maybenull_z_(s)`
    :::column-end:::
    :::column:::
        `_Ret_maybenull_`<br /><br /> `_Ret_maybenull_z_`<br /><br /> `_Ret_null_`<br /><br /> `_Ret_notnull_`<br /><br /> `_Ret_writes_bytes_to_`<br /><br /> `_Ret_writes_bytes_maybenull_`<br /><br /> `_Ret_writes_bytes_to_maybenull_`
    :::column-end:::
:::row-end:::

## <a name="format-string-parameters"></a>Parametry formatu ciągu

- `_Printf_format_string_`Wskazuje, że parametr jest ciągiem formatu do użycia w `printf` wyrażeniu.

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

- `_Scanf_format_string_`Wskazuje, że parametr jest ciągiem formatu do użycia w `scanf` wyrażeniu.

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

- `_Scanf_s_format_string_`Wskazuje, że parametr jest ciągiem formatu do użycia w `scanf_s` wyrażeniu.

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

## <a name="other-common-annotations"></a>Inne typowe adnotacje

### <a name="annotations-and-descriptions"></a>Adnotacje i opisy

- `_In_range_(low, hi)`

     `_Out_range_(low, hi)`

     `_Ret_range_(low, hi)`

     `_Deref_in_range_(low, hi)`

     `_Deref_out_range_(low, hi)`

     `_Deref_inout_range_(low, hi)`

     `_Field_range_(low, hi)`

     Parametr, pole lub wynik znajduje się w zakresie (włącznie) od `low` do `hi` . Równoważne `_Satisfies_(_Curr_ >= low && _Curr_ <= hi)` , które jest stosowane do obiektu z adnotacjami wraz z odpowiednimi warunkami stanu sprzed lub po stanie.

    > [!IMPORTANT]
    > Chociaż nazwy zawierają wartości "in" i "out", semantyka `_In_` i `_Out_` **nie** mają zastosowania do tych adnotacji.

- `_Pre_equal_to_(expr)`

     `_Post_equal_to_(expr)`

     Wartość z adnotacjami jest dokładnie `expr` . Równoważne `_Satisfies_(_Curr_ == expr)` , które jest stosowane do obiektu z adnotacjami wraz z odpowiednimi warunkami stanu sprzed lub po stanie.

- `_Struct_size_bytes_(size)`

     Dotyczy deklaracji klasy lub struktury. Wskazuje, że prawidłowy obiekt tego typu może być większy niż zadeklarowany typ, z liczbą bajtów podawaną przez `size` . Na przykład:

     `typedef _Struct_size_bytes_(nSize) struct MyStruct {    size_t nSize;    ... };`

     Rozmiar buforu w bajtach parametru `pM` typu `MyStruct *` jest następnie traktowany jako:

     `min(pM->nSize, sizeof(MyStruct))`

## <a name="see-also"></a>Zobacz też

- [Korzystanie z adnotacji SAL w celu zmniejszenia liczby defektów kodu C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)
- [Poznanie SAL](../code-quality/understanding-sal.md)
- [Zachowanie funkcji dodawania adnotacji](../code-quality/annotating-function-behavior.md)
- [Dodawanie adnotacji struktur i klas](../code-quality/annotating-structs-and-classes.md)
- [Dodawanie adnotacji do zachowania blokującego](../code-quality/annotating-locking-behavior.md)
- [Określanie miejsca i warunków stosowania adnotacji](../code-quality/specifying-when-and-where-an-annotation-applies.md)
- [Funkcje wewnętrzne](../code-quality/intrinsic-functions.md)
- [Najlepsze rozwiązania i przykłady](../code-quality/best-practices-and-examples-sal.md)
