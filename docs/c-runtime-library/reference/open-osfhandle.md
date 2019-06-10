---
title: _open_osfhandle
ms.date: 05/21/2019
apiname:
- _open_osfhandle
apilocation:
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
apitype: DLLExport
f1_keywords:
- _open_osfhandle
- open_osfhandle
helpviewer_keywords:
- open_osfhandle function
- file handles [C++], associating
- _open_osfhandle function
ms.assetid: 30d94df4-7868-4667-a401-9eb67ecb7855
ms.openlocfilehash: 9e940844eb5e37755c10999feb294981afc8683a
ms.sourcegitcommit: 8adabe177d557c74566c13145196c11cef5d10d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2019
ms.locfileid: "66821599"
---
# <a name="openosfhandle"></a>_open_osfhandle

Kojarzy deskryptor pliku środowiska wykonawczego języka C z istniejących dojście do pliku systemu operacyjnego.

## <a name="syntax"></a>Składnia

```cpp
int _open_osfhandle (
   intptr_t osfhandle,
   int flags
);
```

### <a name="parameters"></a>Parametry

*osfhandle*<br/>
Uchwyt pliku systemu operacyjnego.

*flagi*<br/>
Typy dozwolone operacje.

## <a name="return-value"></a>Wartość zwracana

W przypadku powodzenia **_open_osfhandle —** zwraca deskryptor pliku środowiska wykonawczego języka C. W przeciwnym razie zwraca wartość -1.

## <a name="remarks"></a>Uwagi

**_Open_osfhandle —** funkcja przydziela deskryptor pliku środowiska wykonawczego języka C. Kojarzy ten deskryptor pliku z uchwyt pliku systemu operacyjnego, które są określone przez *osfhandle*. Aby uniknąć ostrzeżenia kompilatora, należy rzutować *osfhandle* argumentu od **obsługi** do **intptr_t**. *Flagi* argument jest wyrażeniem liczby całkowitej z jedną lub więcej stałych manifestu zdefiniowane w \<fcntl.h >. Możesz użyć operatora bitowego OR ( **&#124;** ) do łączenia dwóch lub więcej stałych manifestu do formularza *flagi* argumentu.

Te stałe manifestu są zdefiniowane w \<fcntl.h >:

|||
|-|-|
| **\_O\_DOŁĄCZANIA** | Umieszcza wskaźnik pliku na koniec pliku przed każdej operacji zapisu. |
| **\_O\_RDONLY** | Otwiera plik do odczytu tylko. |
| **\_O\_TEXT** | Otwiera plik w trybie tekstowym (tłumaczonym). |
| **\_O\_WTEXT** | Otwiera plik w trybie Unicode (przetłumaczone UTF-16). |

**_Open_osfhandle —** wywołanie tym przenosi własność dojście do pliku systemu Win32 do deskryptora pliku. Aby zamknąć pliku otwartego przy użyciu **_open_osfhandle —** , wywołaj [ \_Zamknij](close.md). Dojście do pliku podstawowego systemu operacyjnego jest również zamknięty przez wywołanie **_zamknij**. Nie wywołuj funkcję Win32 **funkcja CloseHandle** w dojściu do oryginalnego. Jeżeli deskryptor pliku jest własnością **pliku &#42;**  strumienia, a następnie wywołania [fclose —](fclose-fcloseall.md) zamyka deskryptor pliku i podstawowego dojścia. W tym przypadku nie wywołuj **_zamknij** na deskryptor pliku lub **funkcja CloseHandle** w dojściu do oryginalnego.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_open_osfhandle**|\<io.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Obsługa plików](../../c-runtime-library/file-handling.md)<br/>
[\_get_osfhandle](get-osfhandle.md)
