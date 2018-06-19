---
title: Obsługa określonego języka | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 6503e0cd-2d3a-4330-a925-8bed8c27c2be
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c6cbfbe6a9b98828a63fb4a092717bfab583e9a2
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32368801"
---
# <a name="language-specific-handler"></a>Obsługa określonego języka
Obsługa określonego języka adres względny znajduje się w UNWIND_INFO, gdy ustawiono flagi UNW_FLAG_EHANDLER lub UNW_FLAG_UHANDLER. Zgodnie z opisem w poprzedniej sekcji, obsługa określonego języka jest wywoływana w ramach wyszukiwania dla obsługi wyjątków lub jako część unwind. Składa się z następujących prototypu:  
  
```  
typedef EXCEPTION_DISPOSITION (*PEXCEPTION_ROUTINE) (  
    IN PEXCEPTION_RECORD ExceptionRecord,  
    IN ULONG64 EstablisherFrame,  
    IN OUT PCONTEXT ContextRecord,  
    IN OUT PDISPATCHER_CONTEXT DispatcherContext  
);  
```  
  
 **ExceptionRecord** dostarcza wskaźnik do rekordu wyjątku, który ma standardową definicję Win64.  
  
 **EstablisherFrame** adres podstawowy alokacji stosu stałej dla tej funkcji.  
  
 **ContextRecord** punkty w czasie (w przypadku obsługi wyjątku) został zgłoszony wyjątek lub bieżący kontekst wyjątku "Odwiń" kontekstu (w przypadku programu obsługi zakończenia).  
  
 **DispatcherContext** wskazuje kontekstu dyspozytora dla tej funkcji. Składa się z następującej definicji:  
  
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
  
 **ControlPc** jest wartością RIP w ramach tej funkcji. Jest to adres wyjątek lub adres, jaką formant pozostanie ustanowienia funkcji. Jest to RIP, która będzie służyć do określenia, czy formant jest w niektórych konstrukcja ochroną w ramach tej funkcji (na przykład bloku __try dla \__try /\__except lub \__try /\__finally).  
  
 **Baza obrazu** jest obrazu podstawowego (adres obciążenia) moduł zawierający tę funkcję, można dodać do 32-bitowe przesunięcia używane we wpisie funkcji i unwind informacji, aby zarejestrować względnych adresów.  
  
 **FunctionEntry** dostaw wskaźnik RUNTIME_FUNCTION funkcji wpis zawierający funkcję i unwind informacji obrazu podstawowego względnych adresów dla tej funkcji.  
  
 **EstablisherFrame** adres podstawowy alokacji stosu stałej dla tej funkcji.  
  
 **TargetIp** dostarcza adres instrukcji opcjonalne, który określa adres kontynuacji unwind. Ten adres jest ignorowana, jeśli **EstablisherFrame** nie jest określona.  
  
 **ContextRecord** wskazuje kontekst wyjątku do użytku przez kod operacji unwind wysyłania/wyjątek systemu.  
  
 **LanguageHandler** wskazuje procedury obsługi language specyficzny dla języka wywoływane.  
  
 **HandlerData** wskazuje dane specyficzne dla języka programu obsługi dla tej funkcji.  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa wyjątków (x64)](../build/exception-handling-x64.md)