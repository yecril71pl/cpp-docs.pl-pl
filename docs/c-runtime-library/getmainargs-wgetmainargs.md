---
title: __getmainargs, __wgetmainargs | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- __wgetmainargs
- __getmainargs
apilocation:
- msvcr100.dll
- msvcrt.dll
- msvcr110_clr0400.dll
- msvcr80.dll
- msvcr110.dll
- msvcr90.dll
- msvcr120.dll
apitype: DLLExport
f1_keywords:
- __wgetmainargs
- __getmainargs
dev_langs:
- C++
helpviewer_keywords:
- __wgetmainargs
- __getmainargs
ms.assetid: f72f54eb-9509-4bdf-8752-40fc49055439
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c323780308d71158bf717898a05f3454fabf0c3d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46030248"
---
# <a name="getmainargs-wgetmainargs"></a>__getmainargs, __wgetmainargs

Wywołuje w wierszu polecenia, a następnie kopiuje argumenty `main()` za pośrednictwem przekazanych wskaźników.

## <a name="syntax"></a>Składnia

```cpp
int __getmainargs(
    int * _Argc,
   char *** _Argv,
   char *** _Env,
   int _DoWildCard,
_startupinfo * _StartInfo);

int __wgetmainargs (
   int *_Argc,
   wchar_t ***_Argv,
   wchar_t ***_Env,
   int _DoWildCard,
   _startupinfo * _StartInfo)

```

#### <a name="parameters"></a>Parametry

`_Argc`<br/>
Liczba całkowita, która zawiera liczbę argumentów, które należy wykonać w `argv`. Parametr `argc` jest zawsze większy lub równy 1.

`_Argv`<br/>
Tablica ciągów zakończonych znakiem null, która reprezentuje argumenty wiersza polecenia wprowadzone przez użytkownika programu. Zgodnie z Konwencją `argv[0]` jest poleceniem, z którym wywoływany jest program, argv [1] jest pierwszym argumentem wiersza polecenia i tak dalej, aż do argv [argc —], która jest zawsze **NULL**. Pierwszym argumentem wiersza polecenia jest zawsze `argv[1]` i jest ostatni z nich `argv[argc - 1]`.

`_Env`<br/>
Tablica ciągów reprezentujących zestaw zmiennych w środowisku użytkownika. Ta tablica jest zakończona **NULL** wpisu.

`_DoWildCard`<br/>
Liczba całkowita, jeśli ustawione na 1 rozwija symboli wieloznacznych w argumentach wiersza polecenia lub jeśli nie robi nic, ustaw wartość 0.

`_StartInfo`<br/>
Inne informacje, które zostaną przekazane do biblioteki DLL CRT.

## <a name="return-value"></a>Wartość zwracana

0 w przypadku powodzenia; wartość ujemna w przypadku niepowodzenia.

## <a name="remarks"></a>Uwagi

Użyj `__getmainargs` na platformach — do całego znak i `__wgetmainargs` na platformach znaków dwubajtowych (Unicode).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|__getmainargs|internal.h|
|__wgetmainargs|internal.h|