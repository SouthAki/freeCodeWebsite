---
layout: doc
title: 嵌入式系统
description: 在有限的硬件和软件环境下流畅运行
---

# 嵌入式系统

## 概述

嵌入式系统是指集硬件、软件、机械于一体，用来控制、监测或辅助操作机器和设备的装置。在资源受限的环境中，我们需要编写高效、可靠的代码。

## 核心方向

### 硬件基础

- **微控制器编程**：掌握 ARM、AVR、STM32 等主流微控制器
- **外设驱动**：学习 GPIO、UART、I2C、SPI 等通信协议
- **模拟/数字处理**：理解 ADC、DAC 的应用
- **实时系统**：掌握实时操作系统（RTOS）的使用

### 软件优化

- **内存优化**：在有限的 RAM 中编写高效代码
- **性能优化**：通过汇编和硬件操作提升性能
- **功耗管理**：实现低功耗设计，延长电池续航
- **固件开发**：编写和更新设备固件

### 物联网应用

- **传感器集成**：接入各类传感器采集数据
- **无线通信**：掌握 WiFi、Bluetooth、LoRa 等技术
- **云平台对接**：实现设备与云端的数据交互
- **边缘计算**：在设备端进行数据处理和决策

## 学习路线

1. **电子基础**：学习数字电路、模拟电路基础
2. **微控制器入门**：选择一个开发板学习基础编程
3. **外设驱动开发**：逐个学习各种外设的驱动方法
4. **操作系统**：学习 RTOS 的使用和任务调度
5. **项目实战**：设计并实现完整的嵌入式系统
6. **物联网集成**：将设备接入互联网

## 常见应用领域

- **消费电子**：手机、平板、可穿戴设备
- **智能家居**：智能灯、温度控制、安全系统
- **工业控制**：机器人、PLC、工业设备
- **汽车电子**：车载系统、传感器、控制单元
- **医疗设备**：心电监护、血糖仪、呼吸机
- **农业物联网**：环境监测、精准灌溉

## 开发工具

- **IDE**：Keil MDK、IAR Embedded Workbench、STM32CubeIDE
- **编程语言**：C、C++、汇编
- **调试工具**：JTAG、SWD、Logic Analyzer
- **仿真器**：Proteus、Keil Simulator

## 最佳实践

- 写简洁、易懂的代码
- 充分利用硬件特性
- 进行充分的测试和验证
- 考虑功耗和性能的平衡
- 设计可升级的架构
- 编写完整的技术文档

## 硬件基础深入

### 微控制器架构

微控制器是一个完整的计算机系统，集成了 CPU、存储器、I/O 接口等多个部分。

#### 常见微控制器平台

**ARM Cortex-M 系列**
- Cortex-M0/M0+：低功耗，适合简单应用
- Cortex-M3/M4：广泛应用，性能和功耗平衡
- Cortex-M7：高性能，用于复杂计算
- Cortex-M33：集成安全特性

**典型应用芯片**
- STM32 系列（ST Microelectronics）
- NRF52 系列（Nordic）
- ESP32（Espressif）
- ATSAMD21（Microchip）

#### 芯片选型指南

选择合适的微控制器需要考虑多个因素：

```
┌─────────────────────────────────────┐
│   应用需求分析                        │
├─────────────────────────────────────┤
│ • 功能需求（GPIO、外设数量）          │
│ • 性能要求（CPU 主频）              │
│ • 存储空间（Flash、RAM）             │
│ • 功耗要求（工作电流、待机电流）     │
│ • 集成功能（ADC、DAC、通信接口）     │
│ • 成本预算                          │
│ • 开发工具和社区支持                 │
└─────────────────────────────────────┘
```

### 数字逻辑与时序

#### 数字电路基础

```
GPIO（通用输入输出）
├── 输出模式
│   ├── 推挽输出：可以输出高电平或低电平
│   └── 开漏输出：只能输出低电平或高阻
└── 输入模式
    ├── 浮空输入：容易受干扰
    ├── 上拉输入：通过上拉电阻默认为高电平
    └── 下拉输入：通过下拉电阻默认为低电平
```

#### GPIO 控制示例（STM32）

```c
#include "stm32f4xx_hal.h"

// GPIO 初始化
void GPIO_Init(void) {
  // 使能 GPIO 时钟
  __HAL_RCC_GPIOA_CLK_ENABLE();
  
  GPIO_InitTypeDef GPIO_InitStruct = {0};
  
  // 配置 PA5 为输出模式
  GPIO_InitStruct.Pin = GPIO_PIN_5;
  GPIO_InitStruct.Mode = GPIO_MODE_OUTPUT_PP;
  GPIO_InitStruct.Pull = GPIO_NOPULL;
  GPIO_InitStruct.Speed = GPIO_SPEED_FREQ_LOW;
  
  HAL_GPIO_Init(GPIOA, &GPIO_InitStruct);
}

// GPIO 控制
void LED_Toggle(void) {
  HAL_GPIO_TogglePin(GPIOA, GPIO_PIN_5);  // 翻转
  HAL_GPIO_WritePin(GPIOA, GPIO_PIN_5, GPIO_PIN_SET);    // 设置高电平
  HAL_GPIO_WritePin(GPIOA, GPIO_PIN_5, GPIO_PIN_RESET);  // 设置低电平
  uint8_t state = HAL_GPIO_ReadPin(GPIOA, GPIO_PIN_5);   // 读取状态
}
```

### 通信协议

#### UART（串行通信）

UART 是最基本的通信接口，用于微控制器与计算机或其他设备的通信。

```c
// UART 初始化
void UART_Init(void) {
  __HAL_RCC_USART2_CLK_ENABLE();
  __HAL_RCC_GPIOA_CLK_ENABLE();
  
  // 配置 GPIO 引脚
  GPIO_InitTypeDef GPIO_InitStruct = {0};
  GPIO_InitStruct.Pin = GPIO_PIN_2 | GPIO_PIN_3;
  GPIO_InitStruct.Mode = GPIO_MODE_AF_PP;
  GPIO_InitStruct.Pull = GPIO_NOPULL;
  GPIO_InitStruct.Speed = GPIO_SPEED_FREQ_VERY_HIGH;
  GPIO_InitStruct.Alternate = GPIO_AF7_USART2;
  HAL_GPIO_Init(GPIOA, &GPIO_InitStruct);
  
  // 配置 UART
  UART_HandleTypeDef huart2;
  huart2.Instance = USART2;
  huart2.Init.BaudRate = 115200;
  huart2.Init.WordLength = UART_WORDLENGTH_8B;
  huart2.Init.StopBits = UART_STOPBITS_1;
  huart2.Init.Parity = UART_PARITY_NONE;
  huart2.Init.Mode = UART_MODE_TX_RX;
  HAL_UART_Init(&huart2);
}

// 发送数据
void UART_Send(const char *str) {
  HAL_UART_Transmit(&huart2, (uint8_t *)str, strlen(str), 100);
}

// 接收数据
void UART_Receive(uint8_t *data, uint16_t size) {
  HAL_UART_Receive(&huart2, data, size, 100);
}

// 中断接收
void UART_ReceiveIT(uint8_t *data) {
  HAL_UART_Receive_IT(&huart2, data, 1);
}

// UART 中断处理
void HAL_UART_RxCpltCallback(UART_HandleTypeDef *huart) {
  if (huart->Instance == USART2) {
    // 处理接收到的数据
    uint8_t received_data = 0;
    HAL_UART_Receive_IT(&huart2, &received_data, 1);
  }
}
```

#### I2C（两线通信）

I2C 用于连接多个外设，如传感器、EEPROM 等。

```c
// I2C 初始化
void I2C_Init(void) {
  __HAL_RCC_I2C1_CLK_ENABLE();
  __HAL_RCC_GPIOB_CLK_ENABLE();
  
  // 配置引脚
  GPIO_InitTypeDef GPIO_InitStruct = {0};
  GPIO_InitStruct.Pin = GPIO_PIN_8 | GPIO_PIN_9;
  GPIO_InitStruct.Mode = GPIO_MODE_AF_OD;
  GPIO_InitStruct.Pull = GPIO_PULLUP;
  GPIO_InitStruct.Speed = GPIO_SPEED_FREQ_VERY_HIGH;
  GPIO_InitStruct.Alternate = GPIO_AF4_I2C1;
  HAL_GPIO_Init(GPIOB, &GPIO_InitStruct);
  
  // 配置 I2C
  I2C_HandleTypeDef hi2c1;
  hi2c1.Instance = I2C1;
  hi2c1.Init.ClockSpeed = 100000;
  hi2c1.Init.DutyCycle = I2C_DUTYCYCLE_2;
  hi2c1.Init.OwnAddress1 = 0;
  hi2c1.Init.AddressingMode = I2C_ADDRESSINGMODE_7BIT;
  HAL_I2C_Init(&hi2c1);
}

// I2C 读取
HAL_StatusTypeDef I2C_Read(uint8_t addr, uint8_t reg, uint8_t *data, uint16_t len) {
  // 首先写入寄存器地址
  if (HAL_I2C_Master_Transmit(&hi2c1, (addr << 1), &reg, 1, 100) != HAL_OK) {
    return HAL_ERROR;
  }
  // 然后读取数据
  return HAL_I2C_Master_Receive(&hi2c1, (addr << 1) | 1, data, len, 100);
}

// I2C 写入
HAL_StatusTypeDef I2C_Write(uint8_t addr, uint8_t reg, uint8_t *data, uint16_t len) {
  uint8_t buffer[len + 1];
  buffer[0] = reg;
  memcpy(&buffer[1], data, len);
  return HAL_I2C_Master_Transmit(&hi2c1, (addr << 1), buffer, len + 1, 100);
}
```

#### SPI（同步串行通信）

SPI 提供更高的通信速率，适合高速数据传输。

```c
// SPI 初始化
void SPI_Init(void) {
  __HAL_RCC_SPI1_CLK_ENABLE();
  __HAL_RCC_GPIOA_CLK_ENABLE();
  
  // 配置引脚
  GPIO_InitTypeDef GPIO_InitStruct = {0};
  GPIO_InitStruct.Pin = GPIO_PIN_5 | GPIO_PIN_6 | GPIO_PIN_7;
  GPIO_InitStruct.Mode = GPIO_MODE_AF_PP;
  GPIO_InitStruct.Pull = GPIO_NOPULL;
  GPIO_InitStruct.Speed = GPIO_SPEED_FREQ_VERY_HIGH;
  GPIO_InitStruct.Alternate = GPIO_AF5_SPI1;
  HAL_GPIO_Init(GPIOA, &GPIO_InitStruct);
  
  // CS 脚配置
  GPIO_InitStruct.Pin = GPIO_PIN_4;
  GPIO_InitStruct.Mode = GPIO_MODE_OUTPUT_PP;
  HAL_GPIO_Init(GPIOA, &GPIO_InitStruct);
  
  // 配置 SPI
  SPI_HandleTypeDef hspi1;
  hspi1.Instance = SPI1;
  hspi1.Init.Mode = SPI_MODE_MASTER;
  hspi1.Init.Direction = SPI_DIRECTION_2LINES;
  hspi1.Init.DataSize = SPI_DATASIZE_8BIT;
  hspi1.Init.CLKPolarity = SPI_POLARITY_LOW;
  hspi1.Init.CLKPhase = SPI_PHASE_1EDGE;
  hspi1.Init.NSS = SPI_NSS_SOFT;
  hspi1.Init.BaudRatePrescaler = SPI_BAUDRATEPRESCALER_2;
  HAL_SPI_Init(&hspi1);
}

// SPI 发送和接收
void SPI_TransmitReceive(uint8_t *tx_data, uint8_t *rx_data, uint16_t len) {
  HAL_GPIO_WritePin(GPIOA, GPIO_PIN_4, GPIO_PIN_RESET);  // CS 低电平
  HAL_SPI_TransmitReceive(&hspi1, tx_data, rx_data, len, 100);
  HAL_GPIO_WritePin(GPIOA, GPIO_PIN_4, GPIO_PIN_SET);    // CS 高电平
}
```

## 软件优化高级技巧

### 内存管理

嵌入式系统资源受限，必须精心管理内存。

```c
// 静态内存分配
#define BUFFER_SIZE 256
static uint8_t buffer[BUFFER_SIZE];  // 在编译时确定大小

// 动态内存分配（需谨慎）
#include <stdlib.h>

uint8_t *data = (uint8_t *)malloc(BUFFER_SIZE);
if (data == NULL) {
  // 内存分配失败，处理错误
  return;
}
// 使用 data
free(data);
data = NULL;

// 内存池（推荐方式）
typedef struct {
  uint8_t pool[10][BUFFER_SIZE];
  uint8_t available[10];
} MemoryPool;

MemoryPool g_pool;

void MemPool_Init(void) {
  for (int i = 0; i < 10; i++) {
    g_pool.available[i] = 1;
  }
}

uint8_t *MemPool_Alloc(void) {
  for (int i = 0; i < 10; i++) {
    if (g_pool.available[i]) {
      g_pool.available[i] = 0;
      return g_pool.pool[i];
    }
  }
  return NULL;
}

void MemPool_Free(uint8_t *ptr) {
  for (int i = 0; i < 10; i++) {
    if (g_pool.pool[i] == ptr) {
      g_pool.available[i] = 1;
      return;
    }
  }
}
```

### 性能优化

#### 时钟配置

```c
// 配置高速时钟提升性能
void SystemClock_Config(void) {
  RCC_OscInitTypeDef RCC_OscInitStruct = {0};
  RCC_ClkInitTypeDef RCC_ClkInitStruct = {0};
  
  // 启用 HSE（外部高速晶振）
  RCC_OscInitStruct.OscillatorType = RCC_OSCILLATORTYPE_HSE;
  RCC_OscInitStruct.HSEState = RCC_HSE_ON;
  RCC_OscInitStruct.PLL.PLLState = RCC_PLL_ON;
  RCC_OscInitStruct.PLL.PLLSource = RCC_PLLSOURCE_HSE;
  RCC_OscInitStruct.PLL.PLLM = 25;
  RCC_OscInitStruct.PLL.PLLN = 336;
  RCC_OscInitStruct.PLL.PLLP = RCC_PLLP_DIV2;
  RCC_OscInitStruct.PLL.PLLQ = 7;
  
  HAL_RCC_OscConfig(&RCC_OscInitStruct);
  
  // 配置时钟
  RCC_ClkInitStruct.ClockType = RCC_CLOCKTYPE_HCLK | RCC_CLOCKTYPE_PCLK1 | 
                                RCC_CLOCKTYPE_PCLK2;
  RCC_ClkInitStruct.SYSCLKSource = RCC_SYSCLKSOURCE_PLLCLK;
  RCC_ClkInitStruct.AHBCLKDivider = RCC_SYSCLK_DIV1;
  RCC_ClkInitStruct.APB1CLKDivider = RCC_HCLK_DIV4;
  RCC_ClkInitStruct.APB2CLKDivider = RCC_HCLK_DIV2;
  
  HAL_RCC_ClockConfig(&RCC_ClkInitStruct, FLASH_LATENCY_5);
}
```

#### 中断优化

```c
// 使用中断处理高优先级任务
void ADC_Init_DMA(void) {
  // 配置 DMA 以减少 CPU 开销
  DMA_HandleTypeDef hdma_adc1;
  hdma_adc1.Instance = DMA2_Stream0;
  hdma_adc1.Init.Channel = DMA_CHANNEL_0;
  hdma_adc1.Init.Direction = DMA_PERIPH_TO_MEMORY;
  hdma_adc1.Init.PeriphInc = DMA_PINC_DISABLE;
  hdma_adc1.Init.MemInc = DMA_MINC_ENABLE;
  hdma_adc1.Init.PeriphDataAlignment = DMA_PDATAALIGN_HALFWORD;
  hdma_adc1.Init.MemDataAlignment = DMA_MDATAALIGN_HALFWORD;
  hdma_adc1.Init.Mode = DMA_CIRCULAR;
  hdma_adc1.Init.Priority = DMA_PRIORITY_HIGH;
  
  HAL_DMA_Init(&hdma_adc1);
}

// 中断优先级设置
void NVIC_Config(void) {
  HAL_NVIC_SetPriority(USART2_IRQn, 1, 0);      // 高优先级
  HAL_NVIC_EnableIRQ(USART2_IRQn);
  
  HAL_NVIC_SetPriority(TIM2_IRQn, 2, 0);        // 中等优先级
  HAL_NVIC_EnableIRQ(TIM2_IRQn);
}
```

### 功耗管理

```c
// 低功耗睡眠模式
void Low_Power_Sleep(void) {
  // 禁用不必要的外设
  __HAL_RCC_USART1_CLK_DISABLE();
  __HAL_RCC_SPI1_CLK_DISABLE();
  
  // 进入睡眠模式
  HAL_PWR_EnterSLEEPMode(PWR_MAINREGULATOR_ON, PWR_SLEEPENTRY_WFI);
  
  // 从睡眠中唤醒后重新启用外设
  __HAL_RCC_USART1_CLK_ENABLE();
  __HAL_RCC_SPI1_CLK_ENABLE();
}

// 低功耗停止模式
void Low_Power_Stop(void) {
  // 关闭高速振荡器
  __HAL_RCC_HSE_CONFIG(RCC_HSE_OFF);
  
  // 进入停止模式
  HAL_PWR_EnterSTOPMode(PWR_MAINREGULATOR_ON, PWR_STOPENTRY_WFI);
  
  // 从停止中唤醒后重新配置时钟
  SystemClock_Config();
}

// 实时时钟唤醒
void RTC_Wakeup_Init(uint32_t seconds) {
  RTC_HandleTypeDef hrtc;
  hrtc.Instance = RTC;
  
  // 配置 RTC
  HAL_RTC_Init(&hrtc);
  
  // 设置闹钟
  RTC_AlarmTypeDef sAlarm = {0};
  sAlarm.AlarmTime.Hours = 0;
  sAlarm.AlarmTime.Minutes = 0;
  sAlarm.AlarmTime.Seconds = seconds;
  sAlarm.Alarm = RTC_ALARM_A;
  
  HAL_RTC_SetAlarm_IT(&hrtc, &sAlarm, RTC_FORMAT_BIN);
}
```

## 实时操作系统 (RTOS)

### FreeRTOS 基础

FreeRTOS 是一个轻量级的实时操作系统，适合资源受限的嵌入式系统。

```c
#include "FreeRTOS.h"
#include "task.h"
#include "queue.h"
#include "semphr.h"

// 任务定义
void Task_LED(void *pvParameters) {
  while (1) {
    HAL_GPIO_TogglePin(GPIOA, GPIO_PIN_5);
    vTaskDelay(pdMS_TO_TICKS(500));  // 延迟 500ms
  }
}

void Task_UART(void *pvParameters) {
  char message[50];
  while (1) {
    sprintf(message, "Hello FreeRTOS\r\n");
    HAL_UART_Transmit(&huart2, (uint8_t *)message, strlen(message), 100);
    vTaskDelay(pdMS_TO_TICKS(1000));  // 延迟 1s
  }
}

// 主函数初始化 RTOS
int main(void) {
  HAL_Init();
  SystemClock_Config();
  GPIO_Init();
  UART_Init();
  
  // 创建任务
  xTaskCreate(Task_LED, "LED Task", 128, NULL, 2, NULL);
  xTaskCreate(Task_UART, "UART Task", 256, NULL, 1, NULL);
  
  // 启动调度器
  vTaskStartScheduler();
  
  return 0;
}
```

### 队列通信

```c
#include "queue.h"

// 创建队列
QueueHandle_t xQueue;

void main_init(void) {
  // 创建队列：深度为 10，元素大小为 4 字节
  xQueue = xQueueCreate(10, sizeof(uint32_t));
  
  // 创建生产者任务
  xTaskCreate(Producer_Task, "Producer", 128, NULL, 2, NULL);
  
  // 创建消费者任务
  xTaskCreate(Consumer_Task, "Consumer", 128, NULL, 1, NULL);
  
  vTaskStartScheduler();
}

// 生产者任务
void Producer_Task(void *pvParameters) {
  uint32_t data = 0;
  while (1) {
    data++;
    // 发送数据到队列
    xQueueSend(xQueue, &data, portMAX_DELAY);
    vTaskDelay(pdMS_TO_TICKS(100));
  }
}

// 消费者任务
void Consumer_Task(void *pvParameters) {
  uint32_t data;
  while (1) {
    // 从队列接收数据
    if (xQueueReceive(xQueue, &data, pdMS_TO_TICKS(1000)) == pdPASS) {
      printf("Received: %lu\r\n", data);
    }
  }
}
```

### 信号量与互斥量

```c
#include "semphr.h"

// 互斥量用于保护共享资源
SemaphoreHandle_t xMutex;

void Critical_Section_Init(void) {
  xMutex = xSemaphoreCreateMutex();
  
  xTaskCreate(Task1, "Task1", 128, NULL, 2, NULL);
  xTaskCreate(Task2, "Task2", 128, NULL, 2, NULL);
  
  vTaskStartScheduler();
}

// 共享资源
static int shared_counter = 0;

void Task1(void *pvParameters) {
  while (1) {
    // 获取互斥量
    if (xSemaphoreTake(xMutex, portMAX_DELAY) == pdTRUE) {
      // 临界区：保护共享资源
      shared_counter++;
      printf("Task1: %d\r\n", shared_counter);
      
      // 释放互斥量
      xSemaphoreGive(xMutex);
    }
    vTaskDelay(pdMS_TO_TICKS(100));
  }
}

void Task2(void *pvParameters) {
  while (1) {
    if (xSemaphoreTake(xMutex, portMAX_DELAY) == pdTRUE) {
      shared_counter += 2;
      printf("Task2: %d\r\n", shared_counter);
      xSemaphoreGive(xMutex);
    }
    vTaskDelay(pdMS_TO_TICKS(150));
  }
}
```

## 物联网与边缘计算

### WiFi 连接

```c
// 使用 ESP32 的 WiFi 功能
#include "esp_wifi.h"
#include "esp_event.h"

void wifi_event_handler(void* arg, esp_event_base_t event_base,
                       int32_t event_id, void* event_data) {
  if (event_base == WIFI_EVENT && event_id == WIFI_EVENT_STA_START) {
    esp_wifi_connect();
  } else if (event_base == IP_EVENT && event_id == IP_EVENT_STA_GOT_IP) {
    ip_event_got_ip_t* event = (ip_event_got_ip_t*) event_data;
    printf("Got IP: " IPSTR "\n", IP2STR(&event->ip_info.ip));
  }
}

void wifi_init_sta(void) {
  esp_netif_init();
  esp_event_loop_create_default();
  esp_netif_create_default_wifi_sta();
  
  wifi_init_config_t cfg = WIFI_INIT_CONFIG_DEFAULT();
  esp_wifi_init(&cfg);
  
  esp_event_handler_register(WIFI_EVENT, ESP_EVENT_ANY_ID, &wifi_event_handler, NULL);
  esp_event_handler_register(IP_EVENT, IP_EVENT_STA_GOT_IP, &wifi_event_handler, NULL);
  
  wifi_config_t wifi_config = {
    .sta = {
      .ssid = "SSID",
      .password = "PASSWORD",
    },
  };
  
  esp_wifi_set_mode(WIFI_MODE_STA);
  esp_wifi_set_config(WIFI_IF_STA, &wifi_config);
  esp_wifi_start();
}
```

### 传感器集成

```c
// DHT11 温湿度传感器
typedef struct {
  float temperature;
  float humidity;
} DHT11_Data;

void DHT11_Init(int gpio_pin) {
  gpio_config_t io_conf = {
    .pin_bit_mask = (1ULL << gpio_pin),
    .mode = GPIO_MODE_OUTPUT_OD,
    .pull_up_en = GPIO_PULLUP_ENABLE,
  };
  gpio_config(&io_conf);
}

bool DHT11_Read(int gpio_pin, DHT11_Data *data) {
  uint8_t bits[5] = {0};
  
  // 发送启动信号
  gpio_set_level(gpio_pin, 0);
  esp_rom_delay_us(18000);
  gpio_set_level(gpio_pin, 1);
  esp_rom_delay_us(40);
  
  // 读取 40 位数据
  for (int i = 0; i < 40; i++) {
    // 等待数据位
    while (!gpio_get_level(gpio_pin)) {
      esp_rom_delay_us(1);
    }
    
    esp_rom_delay_us(30);
    uint8_t bit = gpio_get_level(gpio_pin);
    
    bits[i / 8] |= (bit << (7 - (i % 8)));
    
    while (gpio_get_level(gpio_pin)) {
      esp_rom_delay_us(1);
    }
  }
  
  // 检查校验和
  uint8_t checksum = bits[0] + bits[1] + bits[2] + bits[3];
  if (checksum != bits[4]) {
    return false;
  }
  
  // 解析数据
  data->humidity = bits[0] + (bits[1] / 100.0f);
  data->temperature = bits[2] + (bits[3] / 100.0f);
  
  return true;
}
```

### 数据上传到云端

```c
#include "mqtt_client.h"

static esp_mqtt_client_handle_t client;

static void mqtt_event_handler(void *handler_args, esp_event_base_t base, 
                              int32_t event_id, void *event_data) {
  esp_mqtt_event_handle_t event = event_data;
  
  switch (event->event_id) {
    case MQTT_EVENT_CONNECTED:
      printf("MQTT_EVENT_CONNECTED\n");
      esp_mqtt_client_subscribe(client, "home/temperature", 0);
      break;
    case MQTT_EVENT_DISCONNECTED:
      printf("MQTT_EVENT_DISCONNECTED\n");
      break;
    case MQTT_EVENT_PUBLISHED:
      printf("MQTT_EVENT_PUBLISHED, msg_id=%d\n", event->msg_id);
      break;
    default:
      break;
  }
}

void mqtt_init(void) {
  esp_mqtt_client_config_t mqtt_cfg = {
    .broker.address.uri = "mqtt://broker.example.com:1883",
  };
  
  client = esp_mqtt_client_init(&mqtt_cfg);
  esp_mqtt_client_register_event(client, ESP_EVENT_ANY_ID, mqtt_event_handler, NULL);
  esp_mqtt_client_start(client);
}

void publish_sensor_data(float temperature, float humidity) {
  char data[100];
  sprintf(data, "{\"temp\": %.2f, \"humidity\": %.2f}", temperature, humidity);
  
  esp_mqtt_client_publish(client, "home/sensor/data", data, 0, 1, 0);
}
```

## 调试与测试

### 调试技巧

```c
// 串口调试输出
#define DEBUG_ENABLE 1

#if DEBUG_ENABLE
#define DEBUG_PRINT(fmt, ...) \
  do { \
    char debug_buf[256]; \
    snprintf(debug_buf, sizeof(debug_buf), fmt, ##__VA_ARGS__); \
    HAL_UART_Transmit(&huart2, (uint8_t *)debug_buf, strlen(debug_buf), 100); \
  } while(0)
#else
#define DEBUG_PRINT(fmt, ...)
#endif

// 使用示例
void some_function(void) {
  int value = 42;
  DEBUG_PRINT("Value: %d\r\n", value);
}

// 断言
#define ASSERT(condition) \
  do { \
    if (!(condition)) { \
      DEBUG_PRINT("ASSERT FAILED at %s:%d\r\n", __FILE__, __LINE__); \
      while(1); \
    } \
  } while(0)
```

### 单元测试框架

```c
#include "unity.h"

void test_add(void) {
  TEST_ASSERT_EQUAL(5, add(2, 3));
  TEST_ASSERT_EQUAL(0, add(-5, 5));
}

void test_subtract(void) {
  TEST_ASSERT_EQUAL(2, subtract(5, 3));
  TEST_ASSERT_EQUAL(0, subtract(5, 5));
}

int main(void) {
  UNITY_BEGIN();
  RUN_TEST(test_add);
  RUN_TEST(test_subtract);
  return UNITY_END();
}
```

## 常见问题

**Q: 选择哪个开发板入门？**
A: 建议选择以下之一：
1. **Arduino Uno** - 完全的初学者首选，生态系统丰富，教程众多
2. **STM32 Discovery 套件** - 功能强大，成本低廉，适合深度学习
3. **ESP32** - 集成 WiFi 和蓝牙，适合物联网项目
4. **Raspberry Pi Pico** - 价格便宜，支持 MicroPython

**Q: 如何快速定位嵌入式系统的 bug？**
A: 使用多种方法：
1. 使用调试工具（JTAG、SWD）连接专业调试器
2. 添加 LED 指示灯输出调试信息
3. 通过串口打印调试日志
4. 使用逻辑分析仪查看信号波形
5. 在模拟器中进行功能仿真
6. 进行单元测试验证子函数的正确性

**Q: 如何优化代码和功耗？**
A: 多个方面的优化：
1. 使用汇编优化性能关键路径
2. 合理使用硬件加速（DMA、浮点单元）
3. 实现动态功耗管理，根据负载调节工作频率
4. 关闭不使用的模块和外设
5. 使用低功耗睡眠模式
6. 优化中断处理，减少处理时间
7. 选择合适的算法，降低计算复杂度

**Q: 如何管理有限的 RAM？**
A: 
1. 使用静态内存分配而非动态分配
2. 实现内存池管理
3. 避免递归和深层函数调用堆栈
4. 使用环形缓冲区处理数据流
5. 谨慎使用全局变量
6. 检查栈溢出和堆溢出

**Q: RTOS 何时使用，何时不使用？**
A: 
- 使用 RTOS：需要多任务并发，任务优先级管理，实时性要求高
- 不使用 RTOS：简单的顺序任务，资源极其受限，学习初期阶段

---

开启嵌入式开发之旅，让我们一起打造智能硬件！
