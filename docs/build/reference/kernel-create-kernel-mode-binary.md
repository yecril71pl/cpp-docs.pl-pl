---
title: -jądra (Tworzenie jądra trybu Binary) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /kernel
- /kernel-
dev_langs:
- C++
ms.assetid: 6d7fdff0-c3d1-4b78-9367-4da588ce8b05
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bbbae275e751287464e4bf1637ee21aff77fb697
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32379604"
---
# <a name="kernel-create-kernel-mode-binary"></a>/kernel (Utwórz plik binarny trybu jądra)
Tworzy wartość binarną, który może zostać wykonany jądra systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```  
/kernel[-]  
```  
  
## <a name="arguments"></a>Argumenty  
 **/kernel**  
 Kod w bieżącym projekcie są kompilowane i połączone przy użyciu zestawu reguł języka C++, które są specyficzne dla kodu, który zostanie uruchomiony w trybie jądra.  
  
 **/Kernel-**  
 Kod w bieżącym projekcie są kompilowane i połączone bez przy użyciu reguł języka C++, które są specyficzne dla kodu, który zostanie uruchomiony w trybie jądra.  
  
## <a name="remarks"></a>Uwagi  
 Brak nie `#pragma` odpowiednikiem kontroli tej opcji.  
  
 Określanie **/Kernel** opcja nakazuje kompilatorze i konsolidatorze przeprowadzić rozstrzygnięcia są dopuszczalne w trybie jądra, które funkcje języka i upewnij się, że masz wystarczające wszechstronnymi możliwościami, aby zapobiec niestabilności środowiska uruchomieniowego, który jest Unikatowy w trybie jądra C++. Jest to osiągane przez zabronienia korzystanie z funkcji języka C++, które są one w trybie jądra i zapewniając ostrzeżenia dla funkcji języka C++, które są potencjalnie one, ale nie można wyłączyć.  
  
 **/Kernel** opcja ma zastosowanie do kompilatorze i konsolidatorze fazy kompilacji i jest ustawiony na poziomie projektu. Przekaż **/Kernel** przełącznik, aby wskazać kompilator, że wynikowego pliku binarnego, po połączeniu, powinny być załadowane do jądra systemu Windows. Kompilator będzie zawęzić liczne funkcje języka C++ do podzbioru, który jest zgodny z jądra.  
  
 W poniższej tabeli wymieniono zmiany w zachowaniu kompilatora podczas **/Kernel** jest określona.  
  
|Typ zachowania|**/ Kernel** zachowanie|  
|-------------------|---------------------------|  
|Obsługa wyjątków języka C++|Wyłączone. Wszystkie wystąpienia `throw` i `try` słowa kluczowe Emituj wystąpi błąd kompilatora (z wyjątkiem specyfikacji wyjątku `throw()`). Nie **/EH** opcje są zgodne z **/Kernel**, z wyjątkiem **/EH-**.|  
|RTTI|Wyłączone. Wszystkie wystąpienia `dynamic_cast` i `typeid` słowa kluczowe Emituj wystąpi błąd kompilatora, chyba że `dynamic_cast` służy statycznie.|  
|`new` I `delete`|Należy wyraźnie zdefiniować `new()` lub `delete()` operator; kompilator ani środowisko wykonawcze będzie dostarczać definicji domyślnej.|  
  
 Wywoływanie Konwencji, niestandardowe [/GS](../../build/reference/gs-buffer-security-check.md) opcji kompilacji, a wszystkie optymalizacje są dozwolone, gdy używasz **/Kernel** opcji. Ze Śródwierszowaniem przede wszystkim nie ma wpływu na **/Kernel**, o tej samej semantyki honorowane przez kompilator. Jeśli chcesz upewnić się, że `__forceinline` ze śródwierszowaniem kwalifikator jest honorowane, należy się upewnić, że ostrzeżenie [C4714](../../error-messages/compiler-warnings/compiler-warning-level-4-c4714.md) jest włączona, tak aby było wiadomo, gdy określonego `__forceinline` funkcja nie jest wbudowane.  
  
 Gdy są przekazywane przez kompilator **/Kernel** przełącznika go powoduje wstępne definiowanie makro preprocesora, o nazwie `_KERNEL_MODE` i ma wartość **1**. Możesz użyć tego warunkowo skompilować kod na podstawie czy środowiska wykonawczego jest w trybie użytkownika lub w trybie jądra. Na przykład następujący kod określa, że klasa powinna być w segmencie niestronicowalnej pamięci, gdy jest on skompilowany dla wykonywania w trybie jądra.  
  
```cpp  
#ifdef _KERNEL_MODE  
#define NONPAGESECTION __declspec(code_seg("$kerneltext$"))  
#else  
#define NONPAGESECTION  
#endif  
  
class NONPAGESECTION MyNonPagedClass  
{  
   // ...
};  
```  
  
 Niektóre następujących kombinacji architektury docelowej i **/arch** opcji powodowało błąd, gdy są one używane z **/Kernel**:  
  
-   **/ arch: {SSE&#124;SSE2&#124;AVX}** nie są obsługiwane w x86. Tylko **/arch:IA32** jest obsługiwany z **/Kernel** na x86.  
  
-   **/ arch: avx** nie jest obsługiwany z **/Kernel** na x64.  
  
 Kompilowanie z użyciem **/Kernel** przekazuje także **/Kernel** do konsolidatora. Jej ma to wpływ na zachowanie konsolidatora:  
  
-   Konsolidowanie przyrostowe jest wyłączone. Jeśli dodasz **/ incremental** do wiersza polecenia konsolidatora emituje to błąd krytyczny:  
  
     **ŁĄCZA: błąd krytyczny LNK1295: "/ INCREMENTAL" nie jest zgodne z "/ jądra" Specyfikacja; łącze bez "/ INCREMENTAL"**  
  
-   Konsolidator sprawdza każdego pliku obiektu (lub dowolnego członka dołączone archiwum z bibliotek statycznych), aby zobaczyć, czy może on została skompilowana przy użyciu **/Kernel** opcji, ale nie był. Jeśli wszystkie wystąpienia spełnia to kryterium, konsolidator nadal pomyślnie łączy, ale może ostrzeżenie, jak pokazano w poniższej tabeli.  
  
    ||**/ Kernel** obj.|**/Kernel-** obj, MASM obj lub cvtresed|Mieszać z **/Kernel** i **/kernel-** objs|  
    |-|----------------------|-----------------------------------------------|-------------------------------------------------|  
    |**łącze/Kernel**|Tak|Tak|Tak z ostrzeżeniem LNK4257|  
    |**Link**|Tak|Tak|Tak|  
  
     **LNK4257 obiektu nie został skompilowany z/Kernel; Obraz może nie działać.**  
  
 **/Kernel** opcji i **/Driver** opcji działać niezależnie i nie wpływa na drugi.  
  
### <a name="to-set-the-kernel-compiler-option-in-visual-studio"></a>Aby ustawić opcję kompilatora/Kernel w programie Visual Studio  
  
1.  Otwórz **strony właściwości** okno dialogowe dla projektu. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Wybierz **C/C++** folderu.  
  
3.  Wybierz **wiersza polecenia** strony właściwości.  
  
4.  W **dodatkowe opcje** Dodaj `/kernel` lub `/kernel-`.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)