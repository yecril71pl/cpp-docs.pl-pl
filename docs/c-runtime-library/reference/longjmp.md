---
title: longjmp
ms.date: 08/14/2018
api_name:
- longjmp
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- longjmp
helpviewer_keywords:
- restoring stack environment and execution locale
- longjmp function
ms.assetid: 0e13670a-5130-45c1-ad69-6862505b7a2f
ms.openlocfilehash: 4f737818afe7136262362e4fe996745064568758
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218562"
---
# <a name="longjmp"></a>longjmp

Przywraca środowisko stosu i ustawienia regionalne wykonywania ustawione przez `setjmp` wywołanie.

## <a name="syntax"></a>Składnia

```C
void longjmp(
   jmp_buf env,
   int value
);
```

### <a name="parameters"></a>Parametry

*kopert*<br/>
Zmienna, w której jest przechowywane środowisko.

*wartościami*<br/>
Wartość, która ma zostać zwrócona do `setjmp` wywołania.

## <a name="remarks"></a>Uwagi

Funkcja **longjmp** przywraca środowisko stosu i ustawienia regionalne wykonywania wcześniej zapisane w *ENV* przez `setjmp` . `setjmp`i **longjmp** zapewniają sposób wykonywania nielokalnego **`goto`** . zazwyczaj są one używane do przekazywania kontroli wykonywania do kodu obsługi błędów lub odzyskiwania w wcześniej wywołanej procedurze bez używania normalnych konwencji wywołania i powrotu.

Wywołanie `setjmp` powoduje, że bieżące środowisko stosu zostanie zapisane w *ENV*. Kolejne wywołanie **longjmp** przywraca zapisane środowisko i zwraca kontrolę do punktu bezpośrednio po odpowiednim `setjmp` wywołaniu. Wykonywanie jest wznawiane, gdy *wartość* została właśnie zwrócona przez `setjmp` wywołanie. Wartości wszystkich zmiennych (z wyjątkiem zmiennych rejestru), które są dostępne dla rutynowej kontroli, zawierają wartości, które miały po wywołaniu **longjmp** . Wartości zmiennych rejestru są nieprzewidywalne. Wartość zwracana przez program `setjmp` musi być różna od zera. Jeśli *wartość* jest przenoszona jako 0, wartość 1 jest zastępowana w rzeczywistym zwracaniu.

**Specyficzne dla firmy Microsoft**

W programie Microsoft C++ Code w systemie Windows **longjmp** używa tej samej semantyki odwinięcia stosu, co kod obsługi wyjątków. Można bezpiecznie użyć w tych samych miejscach, które mogą być zgłaszane wyjątki C++. Takie użycie nie jest jednak przenośne i zawiera pewne ważne zastrzeżenia.

Wywołaj **longjmp** tylko przed funkcją, która wywołuje metodę `setjmp` Returns; w przeciwnym razie wyniki są nieprzewidywalne.

W przypadku korzystania z programu **longjmp**należy przestrzegać następujących ograniczeń:

- Nie należy zakładać, że wartości zmiennych rejestru pozostaną takie same. Wartości zmiennych rejestru w wywołaniu procedury `setjmp` mogą nie zostać przywrócone do odpowiednich wartości po wykonaniu **longjmp** .

- Nie należy używać **longjmp** do transferowania kontroli z procedury obsługi przerwania, chyba że przerwanie jest spowodowane przez wyjątek zmiennoprzecinkowy. W takim przypadku program może zwrócić z procedury obsługi przerwania za pośrednictwem **longjmp** , jeśli najpierw ponownie zainicjuje pakiet matematyczny zmiennoprzecinkowych przez wywołanie [_fpreset](fpreset.md).

- Nie należy używać **longjmp** do transferowania kontroli z procedury wywołania zwrotnego wywoływanej bezpośrednio lub pośrednio przez kod systemu Windows.

- Jeśli kod jest kompilowany za pomocą **/EHS** lub **/EHsc** , a funkcja, która zawiera wywołanie **longjmp** , **`noexcept`** wówczas obiekty lokalne w tej funkcji mogą nie być destruktory podczas operacji unwindy stosu.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

> [!NOTE]
> W kodzie Portable C++ nie można przyjąć `setjmp` ani `longjmp` obsługiwać semantyki obiektów c++. W `setjmp` / `longjmp` odniesieniu do pary wywołań występuje niezdefiniowane zachowanie, Jeśli zastępowanie `setjmp` i `longjmp` **`catch`** i **`throw`** wywoła wszystkie nieuproszczone destruktory dla wszystkich obiektów automatycznych. W programach w języku C++ zalecamy korzystanie z mechanizmu obsługi wyjątków C++.

Aby uzyskać więcej informacji, zobacz [Korzystanie z setjmp i longjmp](../../cpp/using-setjmp-longjmp.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**longjmp**|\<setjmp.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zapoznaj się z przykładem [_fpreset](fpreset.md).

## <a name="see-also"></a>Zobacz także

[Proces i kontrola środowiska](../../c-runtime-library/process-and-environment-control.md)<br/>
[setjmp](setjmp.md)
