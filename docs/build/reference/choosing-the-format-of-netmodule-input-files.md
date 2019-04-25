---
title: Wybieranie formatu plików wejściowych .netmodule
ms.date: 11/04/2016
ms.assetid: 4653d1bd-300f-4083-86f5-d1a06f44e61c
ms.openlocfilehash: d48bfe84210143db333d1e6b081acf1aa66980cf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62294580"
---
# <a name="choosing-the-format-of-netmodule-input-files"></a>Wybieranie formatu plików wejściowych .netmodule

Plik .obj MSIL (skompilowany przy użyciu [/CLR](clr-common-language-runtime-compilation.md)) mogą być również używane jako plik netmodule.  pliki .obj zawiera metadane i natywnych symboli.  modułów .netmodule zawierają tylko metadane.

Można przekazać pliku .obj MSIL do innych kompilator programu Visual Studio za pośrednictwem/addmodule — opcja kompilatora (ale należy pamiętać, że plik .obj staje się częścią Wynikowy zestaw i muszą być dostarczane z zestawu).  Na przykład Visual C# i Visual Basic należy mieć/addmodule — opcja kompilatora.

> [!NOTE]
>  W większości przypadków należy przekazać do konsolidatora pliku .obj z kompilacji, która utworzony moduł platformy .net.  Przekazywanie pliku .dll lub moduł .netmodule MSIL moduł konsolidatora może spowodować LNK1107.

pliki .obj, wraz z plikami skojarzone .h, które odwołują się za pośrednictwem #include w źródle, Zezwól na aplikacji w języku C++ korzystanie z natywnych typów w module, natomiast w plik netmodule typami zarządzanymi mogą być używane przez aplikację języka C++.  Jeśli próba przekazania pliku .obj, aby #using, informacje o typach natywnych nie będą dostępne. #include plik .h pliku .obj zamiast tego.

Inne kompilatory programu Visual Studio może używać tylko typów zarządzanych z modułu.

Aby ustalić, czy należy używać jako dane wejściowe konsolidatora MSVC modułu .netmodule lub .obj pliku, należy użyć następującego:

- Jeśli tworzysz za pomocą kompilatora Visual Studio, inne niż Visual C++ generuje .netmodule i użyj .netmodule — wejście konsolidatora.

- Jeśli używasz kompilatora MSVC tworzenia modułów i jeśli moduły będzie służyć do tworzenia coś innego niż bibliotekę, użyj plików .obj wytworzone przez kompilator jako dane wejściowe konsolidatora; modułu nie należy używać plik netmodule jako dane wejściowe.

- Jeśli moduły będą służyć do tworzenia biblioteki natywne (niezarządzane), użyj pliki .obj — wejście moduł konsolidatora i wygenerować pliku biblioteki lib.

- Jeśli moduły, które będą używane do tworzenia zarządzanej biblioteki, a wszystkie dane wejściowe modułu konsolidator będzie możliwe do zweryfikowania (utworzone za pomocą/CLR: Safe), użyj pliki .obj — wejście moduł konsolidatora i wygenerować dll (assembly) lub plik biblioteki .netmodule (moduł).

- Jeśli moduły będą służyć do tworzenia zarządzanej biblioteki i jeden lub więcej modułów dane wejściowe konsolidatora, które zostaną wygenerowane za pomocą tylko/CLR, użyj pliki .obj — wejście moduł konsolidatora i wygenerować dll (assembly).  Jeśli chcesz udostępnić typów zarządzanych z biblioteki i czy ma aplikacji w języku C++ korzystanie z natywnych typów w bibliotece biblioteki będzie zawierać pliki .obj dla modułów składnik biblioteki (również można wysłać pliki .h dla każdego modułu dzięki czemu mogą być przywoływane z #include z kodu źródłowego).

## <a name="see-also"></a>Zobacz także

[Pliki .netmodule — wejście konsolidatora](netmodule-files-as-linker-input.md)
