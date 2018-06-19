---
title: '&lt;system_error —&gt; wyliczenia | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- system_error/std::errc
- system_error/std::io_errc
ms.assetid: b21321b7-404a-40de-8777-a85b77c6fa58
ms.openlocfilehash: 4b288d163f5388d2f021b85f29854924a3ed3424
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33856062"
---
# <a name="ltsystemerrorgt-enums"></a>&lt;system_error —&gt; wyliczenia

|||
|-|-|
|[errc —](#errc)|[io_errc](#io_errc)|

## <a name="errc"></a>  errc — wyliczenie

Udostępnia nazwy symbolicznej makr kod błędu zdefiniowany przez Posix w `<errno.h>`.

errc — klasa {address_family_not_supported = EAFNOSUPPORT, address_in_use =: EADDRINUSE, address_not_available = EADDRNOTAVAIL, already_connected = EISCONN, argument_list_too_long = e2big —, argument_out_of_domain = edom —, ZŁY_ADRES = OMYŚLNA, bad_file_ Deskryptor = ebadf —, bad_message = EBADMSG, broken_pipe = EPIPE, connection_aborted = ECONNABORTED, connection_already_in_progress = EALREADY, connection_refused = ECONNREFUSED, connection_reset = ECONNRESET, cross_device_link = EXDEV, destination_ address_required = EDESTADDRREQ, device_or_resource_busy = EBUSY, directory_not_empty = ENOTEMPTY, executable_format_error = enoexec —, file_exists = eexist —, file_too_large = EFBIG, filename_too_long = ENAMETOOLONG, function_not_supported = ENOSYS, host_unreachable =: EHOSTUNREACH, identifier_removed = EIDRM, illegal_byte_sequence = eilseq —, inappropriate_io_control_operation = ENOTTY przerwane = EINTR, invalid_argument — = einval —, invalid_seek = ESPIPE, io_error = EIO, is_a_directory = EISDIR, message_size = EMSGSIZE, network_down =: ENETDOWN, network_reset = ENETRESET, network_unreachable = ENETUNREACH, no_buffer_space = ENOBUFS, no_child_process = echild —, no_link = ENOLINK, no_lock_available = ENOLCK, no_message_available = ENODATA, no_ komunikat = ENOMSG, no_protocol_option = ENOPROTOOPT, no_space_on_device = enospc —, no_stream_resources = ENOSR, no_such_device_or_address = ENXIO, no_such_device = ENODEV, no_such_file_or_directory = enoent —, no_such_process = ESRCH, not_a_directory = ENOTDIR, not_a_socket = ENOTSOCK, not_a_stream = ENOSTR, not_connected = ENOTCONN, not_enough_memory = enomem —, not_supported = ENOTSUP, operation_canceled = ECANCELED, operation_in_progress = EINPROGRESS, operation_not_permitted = EPERM, operation_ NOT_SUPPORTED = EOPNOTSUPP, operation_would_block = EWOULDBLOCK, owner_dead = EOWNERDEAD, permission_denied = eacces —, protocol_error = EPROTO, protocol_not_supported = EPROTONOSUPPORT, read_only_file_system = EROFS, resource_deadlock_would_occur = EDEADLK, resource_unavailable_try_again = eagain —, result_out_of_range = erange —, state_not_recoverable = ENOTRECOVERABLE, stream_timeout = ETIME, text_file_busy = ETXTBSY, timed_out =: ETIMEDOUT, too_many_files_open_in_system = ENFILE, too_many_ files_open = emfile —, too_many_links = EMLINK, too_many_synbolic_link_levels = ELOOP, value_too_large = EOVERFLOW, wrong_protocol_type = EPROTOTYPE,};

### <a name="remarks"></a>Uwagi

## <a name="io_errc"></a>  io_errc — wyliczenie

Udostępnia nazwy symbolicznej dla warunków błędu w \<iostream >. Może służyć do tworzenia [error_condition —](../standard-library/error-condition-class.md) obiektów, które ma być porównywana z wartością zwracaną przez [ios_base::failure](../standard-library/ios-base-class.md#failure) `code()` funkcji.

io_errc — klasa {strumienia = 1};

### <a name="remarks"></a>Uwagi

Zarówno [std::make_error_code()](../standard-library/system-error-functions.md#make_error_code) i [std::make_error_condition()](../standard-library/system-error-functions.md#make_error_condition) są przeciążone dla tego wyliczenia.

`ios_base::failure` może zawierać innych niż kategorie kody błędów `error_condition`.

### <a name="example"></a>Przykład

```cpp
// io_errc.cpp
// cl.exe /nologo /W4 /EHsc /MTd

#include <iostream>

using namespace std;

int main()
{
    cin.exceptions(ios::failbit | ios::badbit);

    try {
        cin.rdbuf(nullptr); // throws io_errc::stream
    }
    catch (ios::failure& e) {
        cerr << "ios failure caught: ";
        if (e.code() == make_error_condition(io_errc::stream)) {
            cerr << "io_errc stream error condition" << endl;
        }
        else {
            cerr << "unmatched error condition code " << e.code() << endl;
        }
    }
}
```

## <a name="see-also"></a>Zobacz także

[<system_error>](../standard-library/system-error.md)<br/>
