---
title: Obsługa określonego języka
ms.date: 11/04/2016
ms.assetid: 6503e0cd-2d3a-4330-a925-8bed8c27c2be
ms.openlocfilehash: f355c0578cdf898dbe8880b2c839cac5634dcbf4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50596335"
---
# <a name="language-specific-handler"></a>Obsługa określonego języka

Adres względny Obsługa określonego języka jest obecny w UNWIND_INFO, zawsze wtedy, gdy ustawiono flagi UNW_FLAG_EHANDLER lub UNW_FLAG_UHANDLER. Zgodnie z opisem w poprzedniej sekcji, obsługa określonego języka jest wywoływana w ramach wyszukiwania dla obsługi wyjątków lub jako część unwind. Ma poniższy prototyp:

```
typedef EXCEPTION_DISPOSITION (*PEXCEPTION_ROUTINE) (
    IN PEXCEPTION_RECORD ExceptionRecord,
    IN ULONG64 EstablisherFrame,
    IN OUT PCONTEXT ContextRecord,
    IN OUT PDISPATCHER_CONTEXT DispatcherContext
);
```

**ExceptionRecord** dostarcza wskaźnik do rekordu wyjątku, który standardowej definicji Win64.

**EstablisherFrame** to adres podstawowy alokacji stosu stałą dla tej funkcji.

**ContextRecord** wskazuje kontekst wyjątku na czas (w przypadku obsługi wyjątku) został zgłoszony wyjątek lub bieżącego "Odwiń" kontekstu (w przypadku programu obsługi zakończenia).

**DispatcherContext** wskazuje kontekst dyspozytora dla tej funkcji. Obowiązują następujące definicje:

```
typedef struct _DISPATCHER_CONTEXT {
    ULONG64 ControlPc;
    ULONG64 ImageBase;
    PRUNTIME_FUNCTION FunctionEntry;
    ULONG64 EstablisherFrame;
    ULONG64 TargetIp;
    PCONTEXT ContextRecord;
    PEXCEPTION_ROUTINE LanguageHandler;
    PVOID HandlerData;
} DISPATCHER_CONTEXT, *PDISPATCHER_CONTEXT;
```

**ControlPc** jest wartością RIP w ramach tej funkcji. Jest to adres wyjątek lub adres, w którym formant pozostanie ustanowienia — funkcja. Jest to RIP, która będzie służyć do określenia, czy kontrolka jest w ramach niektórych chroniona konstrukcja w ramach tej funkcji (na przykład bloku __try dla \__try /\__except lub \__try /\__finally).

**Dla właściwości ImageBase** jest obraz podstawowy (adres obciążenia) moduł zawierający tę funkcję, dodany do przesunięcia 32-bitowe używane we wpisie funkcji do elementu unwind info, aby zarejestrować względnych adresów.

**FunctionEntry** dostarcza wskaźnik RUNTIME_FUNCTION działać wpisu zawierający funkcję, a operacja unwind info obraz podstawowy względnych adresów dla tej funkcji.

**EstablisherFrame** to adres podstawowy alokacji stosu stałą dla tej funkcji.

**TargetIp** dostarcza adres instrukcji opcjonalne, który określa adres kontynuacji unwind. Ten adres jest ignorowana, jeśli **EstablisherFrame** nie zostanie określony.

**ContextRecord** wskazuje kontekst wyjątku, do użytku przez kod operacji unwind/wysyłania wyjątku systemu.

**LanguageHandler** wskazuje procedury obsługi języka specyficznego dla języka, które są wywoływane.

**HandlerData** punktów danych specyficznych dla języka programu obsługi dla tej funkcji.

## <a name="see-also"></a>Zobacz też

[Obsługa wyjątków (x64)](../build/exception-handling-x64.md)