---
title: _environ —, _wenviron — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- environ
- wenviron
- _wenviron
- _environ
dev_langs:
- C++
helpviewer_keywords:
- environ function
- _environ function
- _wenviron function
- process environment
- wenviron function
ms.assetid: 7e639962-6536-47cd-8095-0cbe44a56e03
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5f66e0aa847c0835290895aa7412410b2350d617
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2018
---
# <a name="environ-wenviron"></a>_environ, _wenviron
`_environ` Zmienna jest wskaźnik do tablicy wskaźników do ciągów znaków wielobajtowych, które stanowi środowisko procesu. Tę zmienną globalną jest przestarzała bezpieczniejsze funkcjonalne wersje [getenv_s —, _wgetenv_s —](../c-runtime-library/reference/getenv-s-wgetenv-s.md) i [_putenv_s —, _wputenv_s —](../c-runtime-library/reference/putenv-s-wputenv-s.md), którego należy użyć zamiast zmiennej globalnej. `_environ` jest zadeklarowana w Stdlib.h.  
  
> [!IMPORTANT]
>  Nie można używać tego interfejsu API w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane w aplikacjach platformy uniwersalnej systemu Windows](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
extern char **_environ;  
```  
  
## <a name="remarks"></a>Uwagi  
 W programie, który używa `main` funkcji `_environ` został zainicjowany w momencie uruchamiania programu zgodnie z ustawieniami pobranych z środowiska systemu operacyjnego. Środowisko zawiera jeden lub więcej wpisów w postaci  
  
 `ENVVARNAME``=string`  
  
 `getenv_s` i `putenv_s` użyj `_environ` zmiennej tabeli środowiska modyfikacji i dostępu. Gdy `_putenv` jest wywoływana w celu dodawania lub usuwania ustawień środowiska tabeli środowiska zmienia rozmiar. Jego lokalizacji w pamięci mogą ulec zmianie w zależności od ilości pamięci programu. Wartość `_environ` jest automatycznie dostosowana.  
  
 `_wenviron` Zadeklarowana zmienna, w Stdlib.h jako:  
  
```  
extern wchar_t **_wenviron;  
```  
  
 jest to wersja znaków dwubajtowych `_environ`. W programie, który używa `wmain` funkcji `_wenviron` został zainicjowany w momencie uruchamiania programu zgodnie z ustawieniami pobranych z środowiska systemu operacyjnego.  
  
 W programie, który używa `main`, `_wenviron` jest początkowo **NULL** ponieważ środowisko składa się z ciągów znaków wielobajtowych. W pierwszym wywołaniu `_wgetenv` lub `_wputenv`, odpowiednie środowisko ciąg znaków dwubajtowych jest tworzony i jest wskazywana przez `_wenviron`.  
  
 Podobnie, w programie, który używa `wmain`, `_environ` jest początkowo **NULL** ponieważ środowisko składa się z ciągów znaków dwubajtowych. W pierwszym wywołaniu `_getenv` lub `_putenv`, odpowiednie środowisko ciąg znaków wielobajtowych jest tworzony i jest wskazywana przez `_environ`.  
  
 Gdy w programie jednocześnie istnieją dwie kopie środowiska (MBCS i Unicode), środowiska wykonawczego systemu muszą zachować obydwie kopie spowodować wolniejszy czasu wykonywania. Na przykład, gdy jest wywoływana `_putenv`, wywołanie `_wputenv` również jest wykonywane automatycznie, tak aby odpowiadały ciągów dwóch środowiska.  
  
> [!CAUTION]
>  W rzadkich przypadkach gdy system czasu wykonywania jest obsługę zarówno wersji Unicode, jak i wielobajtowe wersji środowiska, te wersje środowiska dwa może nie odpowiadać dokładnie. To dlatego, chociaż dowolny unikatowy ciąg znaków wielobajtowych mapuje z unikatowym ciągiem Unicode, mapowanie unikatowy ciąg Unicode na ciąg znaków wielobajtowych nie jest zawsze unikatowa. W związku z tym dwa różne ciągi Unicode mogą być mapowane na te same parametry wielobajtowe.  
  
 Sondowanie `_environ` w standardzie Unicode kontekstu jest bez znaczenia gdy [/ / MD](../build/reference/md-mt-ld-use-run-time-library.md) lub `/MDd` połączenia jest używany. Biblioteki DLL CRT typ (wide lub wielobajtowe) programu jest nieznany. Tylko typ wielobajtowe utworzono, ponieważ jest to najbardziej prawdopodobnym scenariuszem.  
  
 Poniższy pseudo-kod przedstawia, jak to możliwe.  
  
```  
int i, j;  
i = _wputenv( "env_var_x=string1" );  // results in the implicit call:  
                                      // putenv ("env_var_z=string1")  
j = _wputenv( "env_var_y=string2" );  // also results in implicit call:  
                                      // putenv("env_var_z=string2")  
```  
  
 Używane w tym przykładzie notacji ciągów znaków nie są literały ciągu języka C; zamiast są symbole zastępcze reprezentujące literał ciągu Unicode w środowisku w `_wputenv` ciągi połączeń i wielobajtowe środowiska w `putenv` wywołania. Pola zastępcze znak`x`"i"`y`"w dwóch odrębnych Unicode ciągów środowiska nie mapują jednoznacznie znaki w bieżącym MBCS. Zamiast tego są mapowane na niektórych znaków MBCS "`z`' który jest domyślnym wynikiem próba konwersji ciągów.  
  
 W związku z tym w środowisku wielobajtowe, wartość "`env_var_z`" po pierwszym wywołaniu niejawne `putenv` byłoby "`string1`", ale ta wartość może zostać nadpisany na drugi niejawne wywołanie `putenv`, gdy wartość "`env_var_z`" jest wartość "`string2`". Środowisko Unicode (w `_wenviron`) oraz środowisko Wielobajtowe (w `_environ`) w związku z tym będzie różnią się od tej serii wywołania.  
  
## <a name="see-also"></a>Zobacz też  
 [Zmienne globalne](../c-runtime-library/global-variables.md)   
 [getenv —, _wgetenv —](../c-runtime-library/reference/getenv-wgetenv.md)   
 [getenv_s, _wgetenv_s](../c-runtime-library/reference/getenv-s-wgetenv-s.md)   
 [_putenv —, _wputenv —](../c-runtime-library/reference/putenv-wputenv.md)   
 [_putenv_s, _wputenv_s](../c-runtime-library/reference/putenv-s-wputenv-s.md)