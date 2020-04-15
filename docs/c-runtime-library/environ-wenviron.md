---
title: _environ, _wenviron
ms.date: 11/04/2016
f1_keywords:
- environ
- wenviron
- _wenviron
- _environ
helpviewer_keywords:
- environ function
- _environ function
- _wenviron function
- process environment
- wenviron function
ms.assetid: 7e639962-6536-47cd-8095-0cbe44a56e03
ms.openlocfilehash: 8d67947c93d1387bfdc38c3bae5b3f978024a725
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81349377"
---
# <a name="_environ-_wenviron"></a>_environ, _wenviron

Zmienna `_environ` jest wskaźnikiem do tablicy wskaźników do ciągów znaków wielobajtowych, które stanowią środowisko procesu. Ta zmienna globalna została przestarzała dla bezpieczniejszych wersji funkcjonalnych [getenv_s, _wgetenv_s](../c-runtime-library/reference/getenv-s-wgetenv-s.md) i [_putenv_s, _wputenv_s](../c-runtime-library/reference/putenv-s-wputenv-s.md), które powinny być używane zamiast zmiennej globalnej. `_environ`w stdlib.h.

> [!IMPORTANT]
> Tego interfejsu API nie można używać w aplikacjach wykonywanych w czasie wykonywania systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobjęte w aplikacjach platformy uniwersalnej systemu Windows](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```
extern char **_environ;
```

## <a name="remarks"></a>Uwagi

W programie, który `main` korzysta `_environ` z tej funkcji, jest inicjowany przy uruchamianiu programu zgodnie z ustawieniami zaczerpniętymi ze środowiska systemu operacyjnego. Środowisko składa się z jednego lub więcej wpisów formularza

`ENVVARNAME` `=string`

`getenv_s`i `putenv_s` użyj `_environ` zmiennej, aby uzyskać dostęp i zmodyfikować tabelę środowiska. Gdy `_putenv` jest wywoływana, aby dodać lub usunąć ustawienia środowiska, tabela środowiska zmienia rozmiar. Jego lokalizacja w pamięci może również ulec zmianie, w zależności od wymagań dotyczących pamięci programu. Wartość `_environ` jest odpowiednio dostosowywana automatycznie.

Zmienna, `_wenviron` zadeklarowana w stdlib.h jako:

```
extern wchar_t **_wenviron;
```

jest szerokoznakową `_environ`wersją . W programie, który `wmain` korzysta `_wenviron` z tej funkcji, jest inicjowany przy uruchamianiu programu zgodnie z ustawieniami zaczerpniętymi ze środowiska systemu operacyjnego.

W programie, który `main` `_wenviron` używa , jest początkowo **NULL,** ponieważ środowisko składa się z ciągów znaków wielobajtowych. Przy pierwszym wywołaniu lub `_wgetenv` `_wputenv`, odpowiednie środowisko ciąg szerokich znaków `_wenviron`jest tworzony i jest wskazywowy przez .

Podobnie w programie, który `wmain`używa `_environ` , jest początkowo **NULL,** ponieważ środowisko składa się z ciągów znaków o szerokich znakach. Przy pierwszym wywołaniu lub `_getenv` `_putenv`, odpowiednie środowisko ciąg wieloznakowy jest `_environ`tworzony i jest wskazywowy przez .

Gdy dwie kopie środowiska (MBCS i Unicode) istnieją jednocześnie w programie, system czasu wykonywania musi obsługiwać obie kopie, co powoduje wolniejszy czas wykonywania. Na przykład za każdym `_putenv`razem, `_wputenv` gdy wywołasz , wywołanie jest również wykonywane automatycznie, tak aby dwa parametry środowiska odpowiadały.

> [!CAUTION]
> W rzadkich przypadkach, gdy system czasu wykonywania jest utrzymanie zarówno wersji Unicode i wielobajtowej wersji środowiska, te dwie wersje środowiska może nie odpowiadać dokładnie. Dzieje się tak, ponieważ chociaż dowolny unikatowy ciąg znaków wielobajtowych jest mapowany na unikatowy ciąg Unicode, mapowanie z unikatowego ciągu Unicode do ciągu znaków wielobajtowych niekoniecznie jest unikatowe. W związku z tym dwa różne ciągi Unicode może mapować do tego samego ciągu wielobajtowego.

Sondowanie `_environ` w kontekście Unicode jest `/MDd` bez znaczenia, gdy [/MD](../build/reference/md-mt-ld-use-run-time-library.md) lub powiązania jest używany. Dla biblioteki DLL CRT typ (szeroki lub wielobajtowy) programu jest nieznany. Tylko typ wielobajtowy jest tworzony, ponieważ jest to najbardziej prawdopodobny scenariusz.

Poniższy pseudokod ilustruje, jak to może się zdarzyć.

```
int i, j;
i = _wputenv( "env_var_x=string1" );  // results in the implicit call:
                                      // putenv ("env_var_z=string1")
j = _wputenv( "env_var_y=string2" );  // also results in implicit call:
                                      // putenv("env_var_z=string2")
```

W notacji używanej w tym przykładzie ciągi znaków nie są literałami ciągu C; raczej są symbole zastępcze, które reprezentują literały `_wputenv` ciągu środowiska Unicode w ciągach środowiska wywołania i wielobajtowych ciągów środowiska w `putenv` wywołaniu. Symbole zastępcze`x`znaków '`y`' i ' ' w dwóch różnych ciągach środowiska Unicode nie są mapowane jednoznacznie na znaki w bieżącym MBCS. Zamiast tego obie mapują na`z`jakiś znak MBCS ' ', który jest domyślnym wynikiem próby konwersji ciągów.

Tak więc w środowisku wielobajtowym wartość`env_var_z`" po `putenv` pierwszym`string1`niejawnym wywołaniu będzie " ", ale ta `putenv`wartość zostanie zastąpiona w drugim niejawne wywołanie , gdy wartość "`env_var_z`" jest ustawiona na "`string2`". Środowisko Unicode (w) `_wenviron`i środowisko wielobajtowe (w) `_environ`różnią się zatem po tej serii wywołań.

## <a name="see-also"></a>Zobacz też

[Zmienne globalne](../c-runtime-library/global-variables.md)<br/>
[getenv, _wgetenv](../c-runtime-library/reference/getenv-wgetenv.md)<br/>
[getenv_s, _wgetenv_s](../c-runtime-library/reference/getenv-s-wgetenv-s.md)<br/>
[_putenv, _wputenv](../c-runtime-library/reference/putenv-wputenv.md)<br/>
[_putenv_s, _wputenv_s](../c-runtime-library/reference/putenv-s-wputenv-s.md)
