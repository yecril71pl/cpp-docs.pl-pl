---
title: _open_osfhandle
ms.date: 05/21/2019
api_name:
- _open_osfhandle
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
ms.openlocfilehash: 2fa2d8190082967d14dd780aa9be7286996b1f9f
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70951215"
---
# <a name="_open_osfhandle"></a>_open_osfhandle

Kojarzy deskryptor pliku C Run-Time z istniejącym dojściem do pliku systemu operacyjnego.

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

*znaczników*<br/>
Dozwolone typy operacji.

## <a name="return-value"></a>Wartość zwracana

Jeśli to się powiedzie, **_open_osfhandle** zwraca deskryptor pliku C Run-Time. W przeciwnym razie zwraca wartość-1.

## <a name="remarks"></a>Uwagi

Funkcja **_open_osfhandle** przydziela deskryptor pliku w czasie wykonywania C. Kojarzy ten deskryptor pliku z dojściem pliku systemu operacyjnego określonym przez *osfhandle*. Aby uniknąć ostrzeżenia kompilatora, należy rzutować argumentu *osfhandle* z **uchwytu** na **intptr_t**. Argument *flags* jest wyrażeniem liczby całkowitej, które zostało utworzone na podstawie co najmniej jednej stałej \<manifestu zdefiniowanej w fcntl. h >. Można użyć operatora bitowego lub ( **&#124;** ), aby połączyć dwie lub więcej stałych manifestu w celu utworzenia argumentu *flags* .

Te stałe manifestu są zdefiniowane w \<fcntl. h >:

|||
|-|-|
| **\_O\_DOŁĄCZENIE** | Umieszcza wskaźnik pliku na końcu pliku przed każdą operacją zapisu. |
| **\_O\_RDONLY** | Otwiera plik tylko do odczytu. |
| **\_O\_TEXT** | Otwiera plik w trybie tekst (przetłumaczony). |
| **\_O\_WTEXT** | Otwiera plik w trybie Unicode (tłumaczone w formacie UTF-16). |

Wywołanie **_open_osfhandle** przenosi własność dojścia pliku Win32 do deskryptora pliku. Aby zamknąć plik otwarty za pomocą **_open_osfhandle**, wywołaj [ \_polecenie Close (Zamknij](close.md)). Dojście do pliku bazowego systemu operacyjnego jest również zamykane przez wywołanie **_close**. Nie wywołuj funkcji **CloseHandle** w systemie Win32 w oryginalnym dojściu. Jeśli deskryptor pliku jest własnością strumienia **pliku &#42;**  , wywołanie [fclose](fclose-fcloseall.md) zamyka zarówno deskryptor pliku, jak i bazowe dojście. W tym przypadku nie należy wywoływać **_close** na deskryptorze pliku ani funkcji **CloseHandle** w oryginalnym dojściu.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_open_osfhandle**|\<io.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Obsługa plików](../../c-runtime-library/file-handling.md)<br/>
[\_get_osfhandle](get-osfhandle.md)
