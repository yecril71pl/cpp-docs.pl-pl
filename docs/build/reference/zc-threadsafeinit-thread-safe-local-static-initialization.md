---
title: '/ Zc: threadsafeinit (wątkowo lokalne statyczne Inicjowanie)'
ms.date: 03/14/2018
f1_keywords:
- threadSafeInit
- /Zc:threadSafeInit
helpviewer_keywords:
- -Zc compiler options (C++)
- threadSafeInit
- Thread-safe Local Static Initialization
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: a0fc4b34-2cf0-45a7-a642-b8afc4ca19f2
ms.openlocfilehash: 92a1bfa5ec3bab2814397d51e35e617b7666c706
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62315706"
---
# <a name="zcthreadsafeinit-thread-safe-local-static-initialization"></a>/ Zc: threadsafeinit (wątkowo lokalne statyczne Inicjowanie)

**/Zc: threadsafeinit** — opcja kompilatora informuje kompilator, aby zainicjować zmienne lokalne statyczne (z zakresem funkcji) w sposób wątkowo bezpieczny, eliminując potrzebę ręcznej synchronizacji. Tylko inicjowania jest metodą o bezpiecznych wątkach. Użycie i modyfikacji statycznych zmiennych lokalnych w wielu wątkach wciąż musi być ręcznie synchronizowane. Ta opcja jest dostępna, począwszy od programu Visual Studio 2015. Domyślnie program Visual Studio umożliwia tej opcji.

## <a name="syntax"></a>Składnia

> **/Zc:threadSafeInit**[**-**]

## <a name="remarks"></a>Uwagi

W C ++ 11 standard za pomocą statycznych zmiennych o zakresie bloku lub okresem magazynu wątku muszą zostać zero zainicjowane przed odbywa się inne metody inicjowania. Inicjowanie występuje, gdy kontrolka najpierw przechodzi przez deklaracja zmiennej. Jeśli wyjątek podczas inicjowania, zmienna jest uznawany za niezainicjowana i inicjowania jest ponowne próby następny formant czasu przechodzi przez deklarację. Jeśli kontrola przechodzi deklaracji wątkom inicjowania bloki wykonania, gdy Inicjowanie zostało zakończone. To zachowanie jest niezdefiniowane, jeżeli formant ponownie przechodzi cyklicznie deklaracji podczas inicjowania. Domyślnie program Visual Studio od wersji programu Visual Studio 2015 implementuje to zachowanie standardowego. To zachowanie może być jawnie określone, ustawiając **/Zc: threadsafeinit** — opcja kompilatora.

**/Zc: threadsafeinit** — opcja kompilatora jest domyślnie włączone. [/ Permissive-](permissive-standards-conformance.md) opcji nie ma wpływu na **/Zc: threadsafeinit**.

Wątkowo Inicjowanie statyczne zmienne lokalne, zależy od kodu implementowanych w biblioteki czasu wykonywania języka Universal C (UCRT). Aby uniknąć tworzenia zależności UCRT lub zachować zachowanie nie wątkowo inicjowanie wersji programu Visual Studio przed Visual Studio 2015, użyj **threadsafeinit** opcji. Jeśli wiesz, że bezpieczeństwo wątków nie jest wymagane, użyj tej opcji, aby wygenerować kod nieco mniejszy, szybszy wokół statyczne deklaracji lokalnego.

Statyczne zmienne lokalne wątków użyj lokalny magazyn wątków (TLS) wewnętrznie, aby zapewnić wydajne wykonywanie, gdy statyczny został już zainicjowany. Implementacja tej funkcji zależy od funkcji obsługi systemu operacyjnego Windows w systemach Windows Vista i nowszych systemach operacyjnych. Windows XP, Windows Server 2003 i starszych systemów operacyjnych nie jest to obsługiwane, nie pobieraj poprawę wydajności. Te systemy operacyjne mieć niższy limit na liczbę sekcji TLS, które mogą być ładowane. Przekroczenie TLS sekcji limit może spowodować awarię. Jeśli jest to problem w kodzie, szczególnie w kodzie, który należy uruchomić w starszych systemach operacyjnych, należy użyć **threadsafeinit** można wyłączyć kod inicjujący metodą o bezpiecznych wątkach.

Aby uzyskać więcej informacji na temat problemów ze zgodnością w języku Visual C++, zobacz [niestandardowe zachowanie](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Z **konfiguracje** menu rozwijanym, wybierz polecenie **wszystkie konfiguracje**.

1. Wybierz **właściwości konfiguracji** > **C/C++** > **wiersza polecenia** stronę właściwości.

1. Modyfikowanie **dodatkowe opcje** właściwości do uwzględnienia **/Zc: threadsafeinit** lub **threadsafeinit** , a następnie wybierz **OK**.

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)<br/>
[/Zc (Zgodność)](zc-conformance.md)<br/>
