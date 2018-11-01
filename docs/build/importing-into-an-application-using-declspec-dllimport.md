---
title: Importowanie do aplikacji przy użyciu atrybutu __declspec(dllimport)
ms.date: 11/04/2016
f1_keywords:
- __declspec
- dllimport
helpviewer_keywords:
- __declspec(dllimport) keyword [C++]
- importing DLLs [C++], __declspec(dllimport)
ms.assetid: edb4da4e-f83a-44cf-a668-9239d49dbe42
ms.openlocfilehash: 925cd588c1851c6fb135fffbb83e9cfd680bea28
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50610477"
---
# <a name="importing-into-an-application-using-declspecdllimport"></a>Importowanie do aplikacji przy użyciu atrybutu __declspec(dllimport)

Program, który używa symboli publicznych, zdefiniowane przez bibliotekę DLL jest nazywany je zaimportować. Po utworzeniu pliki nagłówkowe dla aplikacji korzystających z biblioteki dll do kompilacji, użyj **__declspec(dllimport)** w deklaracjach symboli publicznych. Słowo kluczowe **__declspec(dllimport)** działa, czy w przypadku eksportowania za pomocą plików .def lub za pomocą **__declspec(dllexport)** — słowo kluczowe.

Aby zwiększyć czytelność kodu, zdefiniuj makro dla **__declspec(dllimport)** , a następnie użyj makra do deklarowania każdy symbol zaimportowane:

```
#define DllImport   __declspec( dllimport )

DllImport int  j;
DllImport void func();
```

Za pomocą **__declspec(dllimport)** jest opcjonalna w deklaracjach funkcji, ale kompilator generuje kod, bardziej wydajne, jeśli używasz tego słowa kluczowego. Jednakże, należy użyć **__declspec(dllimport)** importowania pliku wykonywalnego, dostęp do biblioteki DLL symbole publiczne dane i obiekty. Należy pamiętać, że użytkownicy biblioteki DLL muszą nadal łączyć się z biblioteki importowanej.

Można użyć tego samego pliku nagłówka dla biblioteki DLL i aplikacji klienckiej. Aby to zrobić, należy użyć specjalnego symbol preprocesora, która wskazuje, czy kompilowanie biblioteki DLL lub tworzenia aplikacji klienckiej. Na przykład:

```
#ifdef _EXPORTING
   #define CLASS_DECLSPEC    __declspec(dllexport)
#else
   #define CLASS_DECLSPEC    __declspec(dllimport)
#endif

class CLASS_DECLSPEC CExampleA : public CObject
{ ... class definition ... };
```

## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić?

- [Zainicjuj bibliotekę DLL](../build/run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat?

- [Importowanie i eksportowanie funkcji śródwierszowych](../build/importing-and-exporting-inline-functions.md)

- [Importy wzajemne](../build/mutual-imports.md)

## <a name="see-also"></a>Zobacz też

[Importowanie do aplikacji](../build/importing-into-an-application.md)