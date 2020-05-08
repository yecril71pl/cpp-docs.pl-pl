---
title: _aligned_offset_realloc
ms.date: 4/2/2020
api_name:
- _aligned_offset_realloc
- _o__aligned_offset_realloc
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
- api-ms-win-crt-heap-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- aligned_offset_realloc
- _aligned_offset_realloc
helpviewer_keywords:
- aligned_offset_realloc function
- _aligned_offset_realloc function
ms.assetid: e0263533-991e-41b0-acc9-1b8a51ab9ecd
ms.openlocfilehash: c719f62a089b1c233bac193f3431d0375af826eb
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82910259"
---
# <a name="_aligned_offset_realloc"></a>_aligned_offset_realloc

Zmienia rozmiar bloku pamięci, który został przydzielony do [_aligned_malloc](aligned-malloc.md) lub [_aligned_offset_malloc](aligned-offset-malloc.md).

## <a name="syntax"></a>Składnia

```C
void * _aligned_offset_realloc(
   void *memblock,
   size_t size,
   size_t alignment,
   size_t offset
);
```

### <a name="parameters"></a>Parametry

*memblock*<br/>
Bieżący wskaźnik bloku pamięci.

*size*<br/>
Rozmiar alokacji pamięci.

*struktury*<br/>
Wartość wyrównania, która musi być całkowitą potęgą liczby 2.

*Przesunięcie*<br/>
Przesunięcie alokacji pamięci, aby wymusić wyrównanie.

## <a name="return-value"></a>Wartość zwracana

**_aligned_offset_realloc** zwraca wskaźnik void do ponownie przydzielony blok pamięci (i prawdopodobnie przeniesiony). Wartość zwracana ma wartość **null** , jeśli rozmiar ma wartość zero, a argument buforu nie ma **wartości null**lub jeśli nie ma wystarczającej ilości dostępnej pamięci, aby rozszerzyć blok na dany rozmiar. W pierwszym przypadku, oryginalny blok jest zwolniony. W drugim przypadku oryginalny blok nie zmienia się. Wartość zwracana wskazuje miejsce do magazynowania, które jest gwarantowane odpowiednio wyrównane do przechowywania dowolnego typu obiektu. Aby uzyskać wskaźnik do typu innego niż void, należy użyć rzutowania typu dla zwracanej wartości.

**_aligned_offset_realloc** jest oznaczona `__declspec(noalias)` i `__declspec(restrict)`, co oznacza, że funkcja nie modyfikuje zmiennych globalnych i że zwrócony wskaźnik nie ma aliasu. Aby uzyskać więcej informacji, zobacz [noalias](../../cpp/noalias.md) i [ograniczaj](../../cpp/restrict.md).

## <a name="remarks"></a>Uwagi

Podobnie jak [_aligned_offset_malloc](aligned-offset-malloc.md), **_aligned_offset_realloc** umożliwia wyrównanie struktury do przesunięcia w obrębie struktury.

**_aligned_offset_realloc** jest oparty na **malloc**. Aby uzyskać więcej informacji o korzystaniu z **_aligned_offset_malloc**, zobacz [malloc](malloc.md). Jeśli *memblock* ma **wartość null**, funkcja wywołuje **_aligned_offset_malloc** wewnętrznie.

Ta funkcja ustawia **errno** na **ENOMEM** , jeśli alokacja pamięci nie powiodła się lub żądany rozmiar był większy niż **_HEAP_MAXREQ**. Aby uzyskać więcej informacji na temat **errno**, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). Ponadto **_aligned_offset_realloc** sprawdza poprawność jego parametrów. Jeśli *wyrównanie* nie jest potęgą 2 lub jeśli *przesunięcie* jest większe niż lub równe *rozmiarowi* i zero, ta funkcja wywołuje procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, ta funkcja zwraca **wartość null** i ustawia **errno** na **EINVAL**.

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_aligned_offset_realloc**|\<malloc. h>|

## <a name="example"></a>Przykład

Aby uzyskać więcej informacji, zobacz [_aligned_malloc](aligned-malloc.md).

## <a name="see-also"></a>Zobacz też

[Wyrównywanie danych](../../c-runtime-library/data-alignment.md)<br/>
