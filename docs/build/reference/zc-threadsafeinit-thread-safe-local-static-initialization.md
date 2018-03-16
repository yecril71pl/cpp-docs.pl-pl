---
title: "/Zc:threadSafeInit (wątkowo lokalnego statycznego inicjowania) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 03/14/2018
ms.technology:
- cpp-tools
ms.topic: article
f1_keywords:
- threadSafeInit
- /Zc:threadSafeInit
dev_langs:
- C++
helpviewer_keywords:
- -Zc compiler options (C++)
- threadSafeInit
- Thread-safe Local Static Initialization
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: a0fc4b34-2cf0-45a7-a642-b8afc4ca19f2
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c0a809e0137ccdf03318eab64f5af1db542906c4
ms.sourcegitcommit: 9239c52c05e5cd19b6a72005372179587a47a8e4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2018
---
# <a name="zcthreadsafeinit-thread-safe-local-static-initialization"></a>/Zc:threadSafeInit (wątkowo lokalnego statycznego inicjowania)

**/Zc:threadSafeInit** — opcja kompilatora informuje kompilator, aby zainicjować zmienne lokalne statyczne (zakresem funkcji) w sposób zapewniający obsługę wielowątkowości, eliminując konieczność ręcznej synchronizacji. Tylko Inicjalizacja jest bezpieczne wątkowo. Nadal należy ręcznie zsynchronizować użycia i modyfikacji statycznych zmiennych lokalnych przez wiele wątków. Ta opcja jest dostępna, począwszy od programu Visual Studio 2015. Domyślnie program Visual Studio umożliwia tej opcji.

## <a name="syntax"></a>Składnia

> **/Zc:threadSafeInit**[**-**]

## <a name="remarks"></a>Uwagi

C ++ 11 standardowe zmiennych o zasięgu bloku z static lub okresem magazynu wątku musi być zero zainicjowany przed wprowadzeniem innych inicjowania. Inicjowanie występuje, gdy formant przechodzi najpierw deklaracja zmiennej. Jeśli wyjątek podczas inicjowania, zmienna jest uznawany za odinicjowany i inicjowania jest ponowne próby następnego formantu czasu przechodzi przez deklarację. Jeśli formant przechodzi deklaracji równocześnie inicjowania bloki wykonanie współbieżne podczas inicjowania jest ukończona. Zachowanie jest niezdefiniowana, jeśli formant przechodzi ponownie rekursywnie deklaracji podczas inicjowania. Domyślnie program Visual Studio w programie Visual Studio 2015 implementuje to standardowe zachowanie. To zachowanie może być jawnie określona przez ustawienie **/Zc:threadSafeInit** — opcja kompilatora.

**/Zc:threadSafeInit** — opcja kompilatora jest domyślnie włączone. [/ Ograniczająca-](permissive-standards-conformance.md) opcji nie ma wpływu na **/Zc:threadSafeInit**.

Inicjowanie wątkowo statycznych zmiennych lokalnych zależy od kodu implementowanego w biblioteki wykonawczej Universal C (Biblioteka UCRT). Aby uniknąć przyjmowanie zależności Biblioteka UCRT lub zachować zachowanie inicjowania z systemem innym niż wątkowo wersji programu Visual Studio przed Visual Studio 2015, użyj **/Zc:threadSafeInit-** opcji. Jeśli wiesz, że bezpieczeństwo wątków nie jest wymagane, użyj tej opcji, aby wygenerować kod nieco mniejszy, szybszy wokół statycznych lokalne deklaracje.

Bezpieczne wątkowo statycznych zmiennych lokalnych korzystanie z lokalny magazyn wątków (TLS) do wykonywania wydajne podczas statycznych został już zainicjowany. Implementacja tej funkcji zależy od funkcji obsługi systemu operacyjnego Windows w systemie Windows Vista i nowszych systemów operacyjnych. Windows XP, Windows Server 2003 i starsze systemy operacyjne nie jest to obsługiwane, nie są poprawę wydajności. Te systemy operacyjne także mieć niższy limit na liczbę sekcji TLS, które mogą być ładowane. Powyżej TLS limit sekcji może spowodować awarię. Jeśli jest to problem w kodzie, szczególnie w kodzie, który musi zostać uruchomiony w starszych systemach operacyjnych, użyj **/Zc:threadSafeInit-** wyłączyć kod inicjujący wątkowo.

Aby uzyskać więcej informacji na temat problemów zgodności w programie Visual C++, zobacz [niestandardowe zachowanie](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Z **konfiguracje** rozwijane menu, wybierz **wszystkie konfiguracje**.

1. Wybierz **właściwości konfiguracji** > **C/C++** > **wiersza polecenia** strony właściwości.

1. Modyfikowanie **dodatkowe opcje** właściwości, aby uwzględnić **/Zc:threadSafeInit** lub **/Zc:threadSafeInit-** , a następnie wybierz **OK**.

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)<br/>
[/Zc (Zgodność)](../../build/reference/zc-conformance.md)<br/>
