---
title: /Zc:sizedDealloc (Włącz globalne o rozmiarze dezalokacji funkcje) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 03/06/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- sizedDealloc
- /Zc:sizedDealloc
dev_langs:
- C++
helpviewer_keywords:
- -Zc compiler options (C++)
- sizedDealloc
- Enable Global Sized Deallocation Functions
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: 3a73ace0-4d36-420a-b699-0ca6fc0dd134
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0a912b87240ad37e29cade077b7a93aa1e7886a6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32380966"
---
# <a name="zcsizeddealloc-enable-global-sized-deallocation-functions"></a>/Zc:sizedDealloc (Włącz globalne o rozmiarze dezalokacji funkcje)

**/Zc:sizedDealloc** — opcja kompilatora informuje kompilator, aby preferencyjnie wywołania globalnego `operator delete` lub `operator delete[]` funkcje, które mają drugi parametr typu `size_t` Jeśli rozmiar obiektu nie jest dostępny. Funkcje te mogą używać `size_t` parametru w celu zoptymalizowania wydajności program wycofujący przydzielenia.

## <a name="syntax"></a>Składnia

> **/Zc:sizedDealloc**[**-**]

## <a name="remarks"></a>Uwagi

C ++ 11 standardowe, można zdefiniować statycznych funkcji Członkowskich `operator delete` i `operator delete[]` sekundę, które wymagają `size_t` parametru. Zwykle są one używane w połączeniu z [nowy operator](../../cpp/new-operator-cpp.md) funkcje do zaimplementowania efektywniejsze allocators — i deallocators dla obiekt. Jednak C ++ 11 nie zdefiniował równoważne zestaw funkcji dezalokacji w zakresie globalnym. W języku C ++ 11, dezalokacji globalne funkcje, które mają drugi parametr typu `size_t` są traktowane jako funkcje delete umieszczania. One musi być jawnie wywołane przez przekazanie argumentem rozmiaru.

C ++ 14 standardowe zmienia zachowanie kompilatora. Podczas definiowania globalne `operator delete` i `operator delete[]` drugi parametr typu, które wymagają `size_t`, kompilator preferuje wywoływać te funkcje, gdy element członkowski zakres wersji nie są wywoływane i rozmiar obiektu jest dostępny. Kompilator niejawnie przekazuje argumentem rozmiaru. Wersje jeden argument są wywoływane, gdy kompilator nie może określić rozmiar obiektu cofana. W przeciwnym razie nadal stosowane zwykle reguły dotyczące wybierania wersji funkcji dezalokacji do wywołania. Wywołania funkcji globalnego może być jawnie określona przez poprzedzenie jej operator rozpoznawania zakresów (`::`) do wywołania funkcji cofania alokacji.

Domyślnie program Visual C++ w programie Visual Studio 2015 implementuje ten C ++ 14 standardowe zachowanie. Można to jawnie określić przez ustawienie **/Zc:sizedDealloc** — opcja kompilatora. Ta pozycja reprezentuje potencjalnie fundamentalne zmiany. Użyj **/Zc:sizedDealloc-** opcję, aby zachować poprzednie działanie, na przykład w przypadku kodu definiuje operatory delete umieszczania, korzystających z drugi parametr typu `size_t`. Domyślne implementacje biblioteki programu Visual Studio funkcje dezalokacji globalne, które mają drugi parametr typu `size_t` wywołania wersji jeden parametr. Jeśli kod dostarcza tylko jednym parametrem globalne delete — operator i operator delete [], domyślnej implementacji biblioteka funkcji globalnego cofania alokacji o rozmiarze wywołania funkcji globalnych.

**/Zc:sizedDealloc** — opcja kompilatora jest domyślnie włączone. [/ Ograniczająca-](permissive-standards-conformance.md) opcji nie ma wpływu na **/Zc:sizedDealloc**.

Aby uzyskać więcej informacji na temat problemów zgodności w programie Visual C++, zobacz [niestandardowe zachowanie](../../cpp/nonstandard-behavior.md).

## <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Z **konfiguracje** rozwijane menu, wybierz **wszystkie konfiguracje**.

1. Wybierz **właściwości konfiguracji** > **C/C++** > **wiersza polecenia** strony właściwości.

1. Modyfikowanie **dodatkowe opcje** właściwości, aby uwzględnić **/Zc:sizedDealloc** lub **/Zc:sizedDealloc-** , a następnie wybierz **OK**.

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)<br/>
[/Zc (Zgodność)](../../build/reference/zc-conformance.md)<br/>
