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
ms.openlocfilehash: 56f6f1d06d834ccab68daf859fac065cf215582c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62344333"
---
# <a name="environ-wenviron"></a>_environ, _wenviron

`_environ` Zmienna jest wskaźnikiem do tablicy wskaźników do ciągów znaków wielobajtowych, które tworzą środowisko procesu. Ta zmienna globalna jest przestarzała dla bardziej bezpieczne wersje funkcjonalności [getenv_s —, _wgetenv_s —](../c-runtime-library/reference/getenv-s-wgetenv-s.md) i [_putenv_s, _wputenv_s —](../c-runtime-library/reference/putenv-s-wputenv-s.md), którego należy użyć zamiast zmiennej globalnej. `_environ` jest zadeklarowane w Stdlib.h.

> [!IMPORTANT]
>  Tego API nie można używać w aplikacjach korzystających ze środowiska wykonawczego Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platformy uniwersalnej Windows](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```
extern char **_environ;
```

## <a name="remarks"></a>Uwagi

W programie, który używa `main` funkcji `_environ` jest inicjowana w momencie uruchamiania programu zgodnie z ustawieniami podjęte ze środowiska systemu operacyjnego. Środowisko składa się z co najmniej jeden wpis formularza

`ENVVARNAME``=string`

`getenv_s` i `putenv_s` użyj `_environ` zmiennej tabeli środowiska modyfikacji i dostępu. Gdy `_putenv` jest wywoływana w celu dodawania i usuwania ustawień środowiska tabeli środowiska zmienia rozmiar. Jego lokalizację w pamięci mogą ulec zmianie w zależności od wymagań pamięci programu. Wartość `_environ` automatycznie jest odpowiednio dostosowane.

`_wenviron` Zmiennej zadeklarowane w Stdlib.h jako:

```
extern wchar_t **_wenviron;
```

jest wersją znaków dwubajtowych `_environ`. W programie, który używa `wmain` funkcji `_wenviron` jest inicjowana w momencie uruchamiania programu zgodnie z ustawieniami podjęte ze środowiska systemu operacyjnego.

W programie, który używa `main`, `_wenviron` jest początkowo **NULL** ponieważ środowisko składa się z ciągami znaków wielobajtowych. W pierwszym wywołaniu `_wgetenv` lub `_wputenv`, odpowiednie środowisko ciąg znaków dwubajtowych, zostanie utworzony i jest wskazywany przez `_wenviron`.

Podobnie, w programie, który używa `wmain`, `_environ` jest początkowo **NULL** ponieważ środowisko składa się z ciągami znaków dwubajtowych. W pierwszym wywołaniu `_getenv` lub `_putenv`, odpowiednie środowisko ciąg znaków wielobajtowych zostanie utworzony i jest wskazywany przez `_environ`.

Jeśli dwie kopie środowiska (MBCS i Unicode), jednocześnie istnieją w programie, system środowiska wykonawczego, musisz utrzymywać obu kopiach skutkuje wolniejszego czasu wykonania. Na przykład gdy wywołujesz `_putenv`, wywołanie `_wputenv` również jest wykonywane automatycznie, tak, aby odpowiadać zmiennych środowiskowych dwa.

> [!CAUTION]
>  W rzadkich przypadkach podczas systemu środowiska wykonawczego jest obsługi zarówno Unicode i wielobajtowych wersji środowiska, te wersje dwa środowiska mogą nie odpowiadać dokładnie. To dlatego, chociaż dowolny unikatowy ciąg znaków wielobajtowych jest mapowany na ciąg Unicode unikatowy, mapowanie unikatowy ciąg Unicode na ciąg znaków wielobajtowych nie jest muszą być unikatowe. W związku z tym dwa różne ciągi Unicode mogą być mapowane na ten sam ciąg wielobajtowe.

Sondowanie `_environ` Unicode kontekstu jest całkowicie nieprzydatna gdy [/MD](../build/reference/md-mt-ld-use-run-time-library.md) lub `/MDd` powiązania jest używany. Biblioteki DLL CRT typ (szerokie lub wielobajtowych) programu jest nieznany. Tylko typ wielobajtowych powstaje, ponieważ jest to najbardziej prawdopodobnym scenariuszem.

Poniższy pseudo-kod ilustruje, jak to możliwe.

```
int i, j;
i = _wputenv( "env_var_x=string1" );  // results in the implicit call:
                                      // putenv ("env_var_z=string1")
j = _wputenv( "env_var_y=string2" );  // also results in implicit call:
                                      // putenv("env_var_z=string2")
```

W oznaczenie użyte w tym przykładzie ciągi znaków nie są literały ciągu języka C; przeciwnie są one symboli zastępczych, które reprezentują Literały ciągu Unicode w środowisku w `_wputenv` środowiska wywołania i znaków wielobajtowych ciągi w `putenv` wywołania. Pola zastępcze znak`x`"i"`y`"w dwóch odrębnych Unicode zmiennych środowiskowych nie mapują jednoznacznie znaki w bieżącym MBCS. Zamiast tego są mapowane na niektórych znaków MBCS "`z`" oznacza to wynik domyślny próba konwersji ciągów znaków.

W związku z tym, w środowisku wielobajtowych wartości "`env_var_z`" po pierwszym wywołaniu niejawne `putenv` będzie "`string1`", ale tej wartości zostaną zastąpione na sekundę niejawne wywołanie `putenv`, gdy wartość "`env_var_z`" jest wartość "`string2`". Środowisko Unicode (w `_wenviron`) i wielobajtowych środowiska (w `_environ`) w związku z tym będzie różnić się zgodnie z tej serii wywołań.

## <a name="see-also"></a>Zobacz także

[Zmienne globalne](../c-runtime-library/global-variables.md)<br/>
[getenv, _wgetenv](../c-runtime-library/reference/getenv-wgetenv.md)<br/>
[getenv_s, _wgetenv_s](../c-runtime-library/reference/getenv-s-wgetenv-s.md)<br/>
[_putenv, _wputenv](../c-runtime-library/reference/putenv-wputenv.md)<br/>
[_putenv_s, _wputenv_s](../c-runtime-library/reference/putenv-s-wputenv-s.md)
