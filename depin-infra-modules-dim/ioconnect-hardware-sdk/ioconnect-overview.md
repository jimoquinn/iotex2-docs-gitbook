# ioID-SDK Overview

## Why is ioID-SDK needed?

Many traditional Web2-based IoT businesses are looking for new opportunities in the Web3 space and the ioID-SDK is dedicatedly built to address the pain points during this transition.

### Heterogeneity of Smart Devices

Smart devices used in today's IoT businesses vary in terms of chip architectures (e.g., Arm, MIPS, RISC-V, etc.), operating systems (e.g., RTOS, Linux, Android, etc.), peripherals, etc. An IoT development team often faces two major technical hurdles when they try to join the Web3 evolution: 1) Lack of Web3 development kits that support their hardware platforms; and 2) Adoption of different Web3 development kits for different hardware platforms. The first technical challenge prevents an IoT business from being transformed into a Web3 one, whereas the second technical challenge leads to increased learning time and development costs as well as decreased code resuability for developers. The ioID-SDK tackles these challenges by employing an innovative SDK architecture composed of a core framework (CF) and a platform adaptation layer (PAL). While the core framework consists of stable and platform-independent functionalities such as cryptographic algorithms, communication interfaces, data encoding/decoding, etc., the platform adaptation layer handles platform-specific functionalities and accommodates requirements of different embedded systems and communities. This design methodology enables the ioID-SDK to be easily integrated into various smart devices, thereby greatly reducing the development complexity and learning curve.

### Complexity of Web3 Transition

Traditional Web2-based IoT projects are highly centralized and transforming those projects into Web3 ones usually involve significant changes in system architecture and device firmware. Such a lengthy and tedious transformation process has posed a major challenge for Web2-based IoT businesses.The ioID-SDK is able to simplify the changes of existing device firmware by introducing the concept of a standard layer. The standard layer refers to well-known design frameworks, such as embedded operating systems (e.g., FreeRTOS, Zephyr, etc.), POSIX standards, and community-driven code frameworks (e.g., Arduino, Raspberry Pi, ESP32, etc.). The usage of a standard layer can effectively minimize code coupling between the ioID-SDK and original Web2-based IoT project. When the framework provided by the standard layer is used, an IoT developer can easily integrate the ioId-SDK into existing project codebase with only minor code modifications.

To address the pain points that are faced by traditional Web2-based IoT businesses during their Web3 journey, the ioID-SDK is built with a number of salient features.
