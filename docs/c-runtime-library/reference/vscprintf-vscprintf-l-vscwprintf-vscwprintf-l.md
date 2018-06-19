---
title: _vscprintf, _vscprintf_l, _vscwprintf, _vscwprintf_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _vscprintf
- _vscprintf_l
- _vscwprintf_l
- _vscwprintf
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
apitype: DLLExport
f1_keywords:
- vscprintf_l
- vscwpeintf
- _vscwprintf
- _vsctprintf
- _vscprintf
- vscwprintf_l
- vscprintf
- _vscwprintf_l
dev_langs:
- C++
helpviewer_keywords:
- vsctprintf function
- _vscprintf_l function
- _vsctprintf_l function
- _vsctprintf function
- _vscwprintf_l function
- vscwprintf_l function
- _vscprintf function
- _vscwprintf function
- vscwprintf function
- vsctprintf_l function
- formatted text [C++]
- vscprintf function
- vscprintf_l function
ms.assetid: 1bc67d3d-21d5-49c9-ac8d-69e26b16a3c3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4c7b1771b065d7a0acc4db73eb188884086ff3b1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32414171"
---
# <a name="vscprintf-vscprintfl-vscwprintf-vscwprintfl"></a>_vscprintf, _vscprintf_l, _vscwprintf, _vscwprintf_l

Zwraca liczbę znaków w ciągu sformatowany przy użyciu wskaźnika do listy argumentów.

## <a name="syntax"></a>Składnia

```C
int _vscprintf(
   const char *format,
   va_list argptr
);
int _vscprintf_l(
   const char *format,
   locale_t locale,
   va_list argptr
);
int _vscwprintf(
   const wchar_t *format,
   va_list argptr
);
int _vscwprintf_l(
   const wchar_t *format,
   locale_t locale,
   va_list argptr
);
```

### <a name="parameters"></a>Parametry

*Format*<br/>
Ciąg kontroli formatu.

*argptr*<br/>
Wskaźnik do listy argumentów.

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

Aby uzyskać więcej informacji, zobacz [specyfikacje formatu](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

## <a name="return-value"></a>Wartość zwracana

**_vscprintf —** zwraca liczbę znaków, które może być generowane, jeśli ciąg wskazywał przez listę argumentów została drukowaniu i wysyłane do pliku lub buforu przy użyciu określonego formatowania kodów. Wartość zwracana nie zawiera znak końcowy null. **_vscwprintf —** taką samą funkcję wykonuje dla znaki dwubajtowe.

Wersje tych funkcji z **_l** sufiks są identyczne, z wyjątkiem tego, aby używały parametr ustawień regionalnych przekazano zamiast bieżącego ustawienia regionalne wątku.

Jeśli *format* wskaźnika o wartości null, jest program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Zwróć -1, jeśli może kontynuować wykonywania, funkcje i ustaw **errno** do **einval —**.

## <a name="remarks"></a>Uwagi

Każdy *argument* (jeśli istnieje) jest konwertowana według specyfikacji formatu w *format*. Format składa się ze znaków zwykłych i ma tę samą tworzą i działać jako *format* argument [printf](printf-printf-l-wprintf-wprintf-l.md).

> [!IMPORTANT]
> Upewnij się, że jeśli *format* to ciąg zdefiniowany przez użytkownika jest zakończenie wartością null i ma poprawną liczbę i typ parametrów. Aby uzyskać więcej informacji, zobacz [unikanie Overruns buforu](http://msdn.microsoft.com/library/windows/desktop/ms717795).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_vsctprintf —**|**_vscprintf**|**_vscprintf**|**_vscwprintf**|
|**_vsctprintf_l —**|**_vscprintf_l**|**_vscprintf_l**|**_vscwprintf_l**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_vscprintf —**, **_vscprintf_l —**|\<stdio.h>|
|**_vscwprintf —**, **_vscwprintf_l —**|\<stdio.h > lub \<wchar.h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład [vsprintf —](vsprintf-vsprintf-l-vswprintf-vswprintf-l-vswprintf-l.md).

## <a name="see-also"></a>Zobacz także

[We/Wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[fprintf, _fprintf_l, fwprintf, _fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[scanf, _scanf_l, wscanf, _wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[sscanf, _sscanf_l, swscanf, _swscanf_l](sscanf-sscanf-l-swscanf-swscanf-l.md)<br/>
[vprintf, funkcje](../../c-runtime-library/vprintf-functions.md)<br/>
