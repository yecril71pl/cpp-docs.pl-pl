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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 9fbe4a4079fcbb8414e09d0f7dd814a3957e0822
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82910676"
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

*flagi*<br/>
Dozwolone typy operacji.

## <a name="return-value"></a>Wartość zwracana

Jeśli to się powiedzie, **_open_osfhandle** zwraca deskryptor pliku C Run-Time. W przeciwnym razie zwraca wartość-1.

## <a name="remarks"></a>Uwagi

Funkcja **_open_osfhandle** przydziela deskryptora pliku w czasie wykonywania C. Kojarzy ten deskryptor pliku z dojściem pliku systemu operacyjnego określonym przez *osfhandle*. Aby uniknąć ostrzeżenia kompilatora, należy rzutować argumentu *osfhandle* z **uchwytu** na **intptr_t**. Argument *flags* jest wyrażeniem liczby całkowitej, które zostało utworzone na podstawie co najmniej jednej stałej \<manifestu zdefiniowanej w fcntl. h>. Można użyć operatora bitowego lub ( **&#124;** ), aby połączyć dwie lub więcej stałych manifestu w celu utworzenia argumentu *flags* .

Te stałe manifestu są zdefiniowane w \<fcntl. h>:

|||
|-|-|
| **\_O\_dołączenie** | Umieszcza wskaźnik pliku na końcu pliku przed każdą operacją zapisu. |
| **\_O\_RDONLY** | Otwiera plik tylko do odczytu. |
| **\_O\_tekst** | Otwiera plik w trybie tekst (przetłumaczony). |
| **\_O\_WTEXT** | Otwiera plik w trybie Unicode (tłumaczone w formacie UTF-16). |

Wywołanie **_open_osfhandle** przenosi własność dojścia pliku Win32 do deskryptora pliku. Aby zamknąć plik otwarty za pomocą **_open_osfhandle**, wywołaj [ \_polecenie Zamknij](close.md). Dojście do pliku bazowego systemu operacyjnego jest również zamykane przez wywołanie **_close**. Nie wywołuj funkcji **CloseHandle** w systemie Win32 w oryginalnym dojściu. Jeśli deskryptor pliku należy do **pliku &#42;** strumienia, wywołanie [fclose](fclose-fcloseall.md) zamyka zarówno deskryptor pliku, jak i bazowe dojście. W tym przypadku nie należy wywoływać **_close** na deskryptorze pliku ani funkcji **CloseHandle** w oryginalnym dojściu.

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_open_osfhandle**|\<IO. h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Obsługa plików](../../c-runtime-library/file-handling.md)<br/>
[\_get_osfhandle](get-osfhandle.md)
