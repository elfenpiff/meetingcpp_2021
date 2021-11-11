# Writing sustainable software. The how and the what!

## Questions:
 * Is the design over-abstracted?

* Is this API easy to use and hard to misuse?
    * Real world example of which uses the type state pattern:
        https://github.com/eclipse-iceoryx/iceoryx/blob/master/iceoryx_hoofs/include/iceoryx_hoofs/posix_wrapper/posix_call.hpp
    * Take a look at the code example in the doxygen documentation inside the @code section

* Can we reduce the error handling?

* Is this API easy to use? Concurrent case.
    * A construct to create a thread safe class out of any arbitrary object:
        https://github.com/eclipse-iceoryx/iceoryx/blob/master/iceoryx_hoofs/include/iceoryx_hoofs/internal/concurrent/smart_lock.hpp
        This was not presented during the talk but is nevertheless helpful when one would like to create threadsafe objects.
        The handling is similar to a shared_ptr

* Does the name fit?
    * string implementation for safety critical systems in C++14:
        https://github.com/eclipse-iceoryx/iceoryx/blob/master/iceoryx_hoofs/include/iceoryx_hoofs/cxx/string.hpp

* Can one produce readable code with this API?

* Can the API be used without documentation?

* What bugs does the API allow?
    * implementation of an optional with monadic methods in C++14:
        https://github.com/eclipse-iceoryx/iceoryx/blob/master/iceoryx_hoofs/include/iceoryx_hoofs/cxx/optional.hpp
    * implementation of an expected with monadic methods in C++14:
        https://github.com/eclipse-iceoryx/iceoryx/blob/master/iceoryx_hoofs/include/iceoryx_hoofs/cxx/expected.hpp
    * usage example with monadic methods:
        https://github.com/eclipse-iceoryx/iceoryx/blob/master/iceoryx_examples/icedelivery/iox_publisher.cpp

* Is the API easy to use?
    * C++20 aggregate initialization in action:
        https://github.com/ros-realtime/reference-system/blob/main/autoware_reference_system/include/autoware_reference_system/autoware_system_builder.hpp

* Is the task the code performs clear?
    * C++ semaphore wrapper which distinguishes constructors with structs:
        https://github.com/eclipse-iceoryx/iceoryx/blob/master/iceoryx_hoofs/include/iceoryx_hoofs/posix_wrapper/semaphore.hpp

* Ownership & lifetime - do we use RAII?
    * I know it is undocumented but if you like to go deeper into the rabbit hole here is something for a rainy sunday afternoon
    * Generic Factory implementation to use it as a basic building block for Attach/Detach, Open/Close, Add/Remove
      APIs
        https://gitlab.com/el.chris/3delch/-/blob/master/include/buildingBlocks/elGenericFactory.hpp
    * Usage:
        https://gitlab.com/el.chris/3delch/-/blob/master/unitTest/src/buildingBlocks/elGenericFactory_test.cpp

 * Is this code extendable?
    * The listener, an implementation based on the reactor pattern to react to a
        wide variety of events in a single thread at a specific point, like epoll or 
        select.
      https://github.com/eclipse-iceoryx/iceoryx/blob/master/iceoryx_posh/include/iceoryx_posh/popo/listener.hpp

    * Uses the idea of storing the template parameter inside of a callable.
