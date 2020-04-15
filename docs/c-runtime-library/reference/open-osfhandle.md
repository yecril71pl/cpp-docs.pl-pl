---
title: _open_osfhandle
ms.date: 4/2/2020
api_name:
- _open_osfhandle
- _o__open_osfhandle
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
- api-ms-win-crt-stdio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _open_osfhandle
- open_osfhandle
helpviewer_keywords:
- open_osfhandle function
- file handles [C++], associating
- _open_osfhandle function
ms.assetid: 30d94df4-7868-4667-a401-9eb67ecb7855
ms.openlocfilehash: 16966bedd80dc90eaa89ee46e6b633a9cf7af74f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338544"
---
# <a name="_open_osfhandle"></a>_open_osfhandle

Kojarzy deskryptor pliku w czasie wykonywania języka C z istniejącym uchwytem pliku systemu operacyjnego.

## <a name="syntax"></a>Składnia

```cpp
int _open_osfhandle (
   intptr_t osfhandle,
   int flags
);
```

### <a name="parameters"></a>Parametry

*osfhandle*<br/>
Dojście do pliku systemu operacyjnego.

*flagi*<br/>
Typy operacji dozwolone.

## <a name="return-value"></a>Wartość zwracana

Jeśli się powiedzie, **_open_osfhandle** zwraca deskryptor pliku w czasie wykonywania języka C. W przeciwnym razie zwraca wartość -1.

## <a name="remarks"></a>Uwagi

Funkcja **_open_osfhandle** przydziela deskryptor pliku w czasie wykonywania języka C. Kojarzy ten deskryptor pliku z uchwytem pliku systemu operacyjnego określonym przez *osfhandle*. Aby uniknąć ostrzeżenia kompilatora, przerzuć argument *osfhandle* z **handle** na **intptr_t**. Argument *flags* jest wyrażeniem liczby całkowitej utworzonym z jednej \<lub więcej stałych manifestu zdefiniowanych w fcntl.h>. Operator bitowy OR **(&#124;** ) służy do łączenia dwóch lub więcej stałych manifestu w celu utworzenia argumentu *flags.*

Te stałe manifestu \<są zdefiniowane w fcntl.h>:

|||
|-|-|
| **\_O\_APPEND** | Umieszcza wskaźnik pliku na końcu pliku przed każdą operacją zapisu. |
| **\_O\_RDONLY** | Otwiera plik tylko do odczytu. |
| **\_O\_TEKST** | Otwiera plik w trybie tekstowym (przetłumaczonym). |
| **\_O\_WTEXT** | Otwiera plik w trybie Unicode (przetłumaczone UTF-16). |

**Wywołanie _open_osfhandle** przenosi własność dojścia pliku Win32 do deskryptora pliku. Aby zamknąć plik otwarty za pomocą **_open_osfhandle**, zadzwoń [ \_zamknij](close.md). Podstawowy uchwyt pliku systemu operacyjnego jest również zamykany przez wywołanie **_close**. Nie należy wywoływać funkcji Win32 **CloseHandle** na oryginalnym dojście. Jeśli deskryptor pliku jest własnością strumienia **FILE &#42;,** [wywołanie fclose](fclose-fcloseall.md) zamyka zarówno deskryptor pliku, jak i podstawowy uchwyt. W takim przypadku nie wywołać **_close** na deskryptor pliku lub **CloseHandle** na oryginalnym dojście.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_open_osfhandle**|\<> io.h|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Obsługa plików](../../c-runtime-library/file-handling.md)<br/>
[\_get_osfhandle](get-osfhandle.md)
