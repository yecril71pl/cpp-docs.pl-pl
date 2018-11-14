---
title: _open_osfhandle
ms.date: 05/29/2018
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
ms.openlocfilehash: f45ca46cae459c8606f88a98d03b64c40e5d5f01
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2018
ms.locfileid: "51327866"
---
# <a name="openosfhandle"></a>_open_osfhandle

Kojarzy deskryptor pliku środowiska wykonawczego języka C z istniejących uchwyt pliku systemu operacyjnego.

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
Typy dozwolone operacje.

## <a name="return-value"></a>Wartość zwracana

W przypadku powodzenia **_open_osfhandle —** zwraca deskryptor pliku środowiska wykonawczego języka C. W przeciwnym razie zwraca wartość -1.

## <a name="remarks"></a>Uwagi

**_Open_osfhandle —** funkcja przydziela deskryptor pliku środowiska wykonawczego języka C i kojarzy ją z określonego przez dojście do pliku systemu operacyjnego *osfhandle*. Aby uniknąć ostrzeżenia kompilatora, należy rzutować *osfhandle* argumentu od **obsługi** do **intptr_t**. *Flagi* argument jest wyrażeniem liczby całkowitej z jedną lub więcej stałych manifestu zdefiniowane w \<fcntl.h >. Gdy dwa lub więcej stałych manifestu są używane do formularza *flagi* argument, stałe są łączone za pomocą operatora bitowego OR ( **&#124;** ).

Te stałe manifestu są zdefiniowane w \<fcntl.h >:

|||
|-|-|
| **\_O\_DOŁĄCZANIA** | Umieszcza wskaźnik pliku na koniec pliku przed każdej operacji zapisu. |
| **\_O\_RDONLY** | Otwiera plik do odczytu tylko. |
| **\_O\_TEXT** | Otwiera plik w trybie tekstowym (tłumaczonym). |
| **\_O\_WTEXT** | Otwiera plik w trybie Unicode (przetłumaczone UTF-16). |

**_Open_osfhandle —** wywołanie tym przenosi własność dojście do pliku systemu Win32 do deskryptora pliku. Aby zamknąć pliku otwartego przy użyciu **_open_osfhandle —**, wywołaj [ \_Zamknij](close.md). Dojście do pliku podstawowego systemu operacyjnego jest również zamknięty przez wywołanie **_zamknij**, więc nie jest konieczne wywołać funkcję Win32 **funkcja CloseHandle** w dojściu do oryginalnego. Jeżeli deskryptor pliku jest własnością **pliku &#42;**  strumienia, następnie wywoływania [fclose —](fclose-fcloseall.md) na tym **pliku &#42;**  strumień zostanie zamknięty deskryptor pliku i podstawowego dojścia. W tym przypadku nie wywołuj **_zamknij** na deskryptor pliku.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_open_osfhandle**|\<io.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Obsługa plików](../../c-runtime-library/file-handling.md)<br/>
