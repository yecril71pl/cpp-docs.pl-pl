---
title: /Zc:sizedDealloc (Włączanie globalnych funkcji dezalokacji)
ms.date: 03/06/2018
f1_keywords:
- sizedDealloc
- /Zc:sizedDealloc
helpviewer_keywords:
- -Zc compiler options (C++)
- sizedDealloc
- Enable Global Sized Deallocation Functions
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: 3a73ace0-4d36-420a-b699-0ca6fc0dd134
ms.openlocfilehash: 160e90f0b068da6fe8330ac97dfd8bda52f05a38
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50536607"
---
# <a name="zcsizeddealloc-enable-global-sized-deallocation-functions"></a>/Zc:sizedDealloc (Włączanie globalnych funkcji dezalokacji)

**/Zc:sizedDealloc** — opcja kompilatora informuje kompilator, aby preferencyjne wywołania globalnego `operator delete` lub `operator delete[]` funkcji, które mają drugi parametr typu `size_t` gdy rozmiar obiektu jest dostępna. Te funkcje mogą używać `size_t` parametru, aby zoptymalizować wydajność program wycofujący przydzielenia.

## <a name="syntax"></a>Składnia

> **/Zc:sizedDealloc**[**-**]

## <a name="remarks"></a>Uwagi

W standardem C ++ 11, może zdefiniować statyczne funkcje Członkowskie `operator delete` i `operator delete[]` , które wymagają sekundy, `size_t` parametru. Zazwyczaj są one używane w połączeniu z [nowy operator](../../cpp/new-operator-cpp.md) funkcji, aby zaimplementować bardziej wydajne alokatorów i deallocators dla obiektu. Jednak C ++ 11 nie definiują równoważne zbiór funkcji dezalokacji w zakresie globalnym. W C ++ 11, globalnych funkcji dezalokacji mające drugi parametr typu `size_t` są traktowane jako funkcje delete umieszczania. One muszą być jawnie wywołane przez przekazanie argumentu rozmiaru.

C ++ 14 standardowa zmienia zachowanie kompilatora. Podczas definiowania globalnego `operator delete` i `operator delete[]` drugi parametr typu, które wymagają `size_t`, kompilator preferuje wywołania tych funkcji, gdy element członkowski zakres wersji nie są wywoływane i rozmiar obiektu jest dostępna. Kompilator przekazuje argumentu rozmiaru niejawnie. Wersje pojedynczy argument są wywoływane, gdy kompilator nie może określić rozmiar obiektu cofany. W przeciwnym razie nadal stosowane zwykle reguły dotyczące wybierania wersję funkcji dezalokacji do wywołania. Wywołania funkcji globalnych, które może być jawnie określone przez dołączenie operatora rozpoznawania zakresu (`::`) do wywołania funkcji dezalokacji.

Domyślnie program Visual C++, począwszy od programu Visual Studio 2015 implementuje C ++ 14 standardowego zachowania. Można to jawnie określić, ustawiając **/Zc:sizedDealloc** — opcja kompilatora. Jest to potencjalnie istotne zmiany. Użyj **/Zc:sizedDealloc-** opcję, aby zachować stare zachowanie, na przykład, gdy kod definiuje operatory delete umieszczania, korzystających z drugim parametrem typu `size_t`. Domyślna implementacja biblioteki programu Visual Studio funkcji dezalokacji globalne, które mają drugi parametr typu `size_t` wywołania wersje jeden parametr. Jeśli Twój kod dostarcza tylko pojedynczego parametru globalnej delete — operator i operator delete [], domyślnej implementacji biblioteka funkcji globalnych dezalokacji wielkości wywołania funkcji globalnych.

**/Zc:sizedDealloc** — opcja kompilatora jest domyślnie włączone. [/ Permissive-](permissive-standards-conformance.md) opcji nie ma wpływu na **/Zc:sizedDealloc**.

Aby uzyskać więcej informacji na temat problemów ze zgodnością w języku Visual C++, zobacz [niestandardowe zachowanie](../../cpp/nonstandard-behavior.md).

## <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Z **konfiguracje** menu rozwijanym, wybierz polecenie **wszystkie konfiguracje**.

1. Wybierz **właściwości konfiguracji** > **C/C++** > **wiersza polecenia** stronę właściwości.

1. Modyfikowanie **dodatkowe opcje** właściwości do uwzględnienia **/Zc:sizedDealloc** lub **/Zc:sizedDealloc-** , a następnie wybierz **OK**.

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)<br/>
[/Zc (Zgodność)](../../build/reference/zc-conformance.md)<br/>
