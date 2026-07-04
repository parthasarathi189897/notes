---
excalidraw-plugin: parsed
---
%%{
  excalidraw
    {
      "projectName": "Kafka Partitions",
      "elements": [
        {
          "id": "partition_topic_box",
          "type": "rectangle",
          "x": 50,
          "y": 20,
          "width": 700,
          "height": 250,
          "strokeColor": "#000000",
          "backgroundColor": "#f0f0f0",
          "strokeWidth": 2
        },
        {
          "id": "partition_topic_label",
          "type": "text",
          "x": 60,
          "y": 30,
          "width": 100,
          "height": 25,
          "text": "Topic: orders",
          "fontSize": 18,
          "fontFamily": 1,
          "textAlign": "left"
        },
        {
          "id": "p0_box",
          "type": "rectangle",
          "x": 60,
          "y": 80,
          "width": 180,
          "height": 150,
          "strokeColor": "#0066cc",
          "backgroundColor": "#e6f2ff",
          "strokeWidth": 2
        },
        {
          "id": "p0_label",
          "type": "text",
          "x": 70,
          "y": 90,
          "width": 160,
          "height": 20,
          "text": "Partition 0",
          "fontSize": 14,
          "fontFamily": 1,
          "fontStyle": "bold"
        },
        {
          "id": "p0_event1",
          "type": "text",
          "x": 70,
          "y": 120,
          "width": 150,
          "height": 15,
          "text": "[o0] key=user_123",
          "fontSize": 12,
          "fontFamily": 3
        },
        {
          "id": "p0_event2",
          "type": "text",
          "x": 70,
          "y": 140,
          "width": 150,
          "height": 15,
          "text": "[o1] key=user_456",
          "fontSize": 12,
          "fontFamily": 3
        },
        {
          "id": "p0_event3",
          "type": "text",
          "x": 70,
          "y": 160,
          "width": 150,
          "height": 15,
          "text": "[o2] key=user_123",
          "fontSize": 12,
          "fontFamily": 3
        },
        {
          "id": "p0_event4",
          "type": "text",
          "x": 70,
          "y": 180,
          "width": 150,
          "height": 15,
          "text": "[o3] key=user_789",
          "fontSize": 12,
          "fontFamily": 3
        },
        {
          "id": "p1_box",
          "type": "rectangle",
          "x": 270,
          "y": 80,
          "width": 180,
          "height": 150,
          "strokeColor": "#0066cc",
          "backgroundColor": "#e6f2ff",
          "strokeWidth": 2
        },
        {
          "id": "p1_label",
          "type": "text",
          "x": 280,
          "y": 90,
          "width": 160,
          "height": 20,
          "text": "Partition 1",
          "fontSize": 14,
          "fontFamily": 1,
          "fontStyle": "bold"
        },
        {
          "id": "p1_event1",
          "type": "text",
          "x": 280,
          "y": 120,
          "width": 150,
          "height": 15,
          "text": "[o0] key=user_222",
          "fontSize": 12,
          "fontFamily": 3
        },
        {
          "id": "p1_event2",
          "type": "text",
          "x": 280,
          "y": 140,
          "width": 150,
          "height": 15,
          "text": "[o1] key=user_888",
          "fontSize": 12,
          "fontFamily": 3
        },
        {
          "id": "p1_event3",
          "type": "text",
          "x": 280,
          "y": 160,
          "width": 150,
          "height": 15,
          "text": "[o2] key=user_222",
          "fontSize": 12,
          "fontFamily": 3
        },
        {
          "id": "p2_box",
          "type": "rectangle",
          "x": 480,
          "y": 80,
          "width": 180,
          "height": 150,
          "strokeColor": "#0066cc",
          "backgroundColor": "#e6f2ff",
          "strokeWidth": 2
        },
        {
          "id": "p2_label",
          "type": "text",
          "x": 490,
          "y": 90,
          "width": 160,
          "height": 20,
          "text": "Partition 2",
          "fontSize": 14,
          "fontFamily": 1,
          "fontStyle": "bold"
        },
        {
          "id": "p2_event1",
          "type": "text",
          "x": 490,
          "y": 120,
          "width": 150,
          "height": 15,
          "text": "[o0] key=user_111",
          "fontSize": 12,
          "fontFamily": 3
        },
        {
          "id": "p2_event2",
          "type": "text",
          "x": 490,
          "y": 140,
          "width": 150,
          "height": 15,
          "text": "[o1] key=user_555",
          "fontSize": 12,
          "fontFamily": 3
        },
        {
          "id": "p2_event3",
          "type": "text",
          "x": 490,
          "y": 160,
          "width": 150,
          "height": 15,
          "text": "[o2] key=user_111",
          "fontSize": 12,
          "fontFamily": 3
        },
        {
          "id": "consumergroup_label",
          "type": "text",
          "x": 60,
          "y": 300,
          "width": 250,
          "height": 20,
          "text": "Consumer Group A reads in parallel:",
          "fontSize": 14,
          "fontFamily": 1,
          "fontStyle": "bold"
        },
        {
          "id": "consumer_a_box",
          "type": "rectangle",
          "x": 80,
          "y": 350,
          "width": 120,
          "height": 60,
          "strokeColor": "#00aa00",
          "backgroundColor": "#e6ffe6",
          "strokeWidth": 2
        },
        {
          "id": "consumer_a_label",
          "type": "text",
          "x": 90,
          "y": 365,
          "width": 100,
          "height": 15,
          "text": "Consumer A",
          "fontSize": 12,
          "fontFamily": 1
        },
        {
          "id": "consumer_a_p",
          "type": "text",
          "x": 90,
          "y": 385,
          "width": 100,
          "height": 15,
          "text": "reads P0",
          "fontSize": 11,
          "fontFamily": 3
        },
        {
          "id": "consumer_b_box",
          "type": "rectangle",
          "x": 250,
          "y": 350,
          "width": 120,
          "height": 60,
          "strokeColor": "#00aa00",
          "backgroundColor": "#e6ffe6",
          "strokeWidth": 2
        },
        {
          "id": "consumer_b_label",
          "type": "text",
          "x": 260,
          "y": 365,
          "width": 100,
          "height": 15,
          "text": "Consumer B",
          "fontSize": 12,
          "fontFamily": 1
        },
        {
          "id": "consumer_b_p",
          "type": "text",
          "x": 260,
          "y": 385,
          "width": 100,
          "height": 15,
          "text": "reads P1",
          "fontSize": 11,
          "fontFamily": 3
        },
        {
          "id": "consumer_c_box",
          "type": "rectangle",
          "x": 420,
          "y": 350,
          "width": 120,
          "height": 60,
          "strokeColor": "#00aa00",
          "backgroundColor": "#e6ffe6",
          "strokeWidth": 2
        },
        {
          "id": "consumer_c_label",
          "type": "text",
          "x": 430,
          "y": 365,
          "width": 100,
          "height": 15,
          "text": "Consumer C",
          "fontSize": 12,
          "fontFamily": 1
        },
        {
          "id": "consumer_c_p",
          "type": "text",
          "x": 430,
          "y": 385,
          "width": 100,
          "height": 15,
          "text": "reads P2",
          "fontSize": 11,
          "fontFamily": 3
        },
        {
          "id": "arrow_p0_c",
          "type": "arrow",
          "x": 160,
          "y": 240,
          "x2": 140,
          "y2": 350,
          "strokeColor": "#333333",
          "strokeWidth": 2,
          "endArrowType": "dot"
        },
        {
          "id": "arrow_p1_b",
          "type": "arrow",
          "x": 360,
          "y": 240,
          "x2": 310,
          "y2": 350,
          "strokeColor": "#333333",
          "strokeWidth": 2,
          "endArrowType": "dot"
        },
        {
          "id": "arrow_p2_a",
          "type": "arrow",
          "x": 570,
          "y": 240,
          "x2": 480,
          "y2": 350,
          "strokeColor": "#333333",
          "strokeWidth": 2,
          "endArrowType": "dot"
        },
        {
          "id": "throughput_label",
          "type": "text",
          "x": 60,
          "y": 450,
          "width": 600,
          "height": 30,
          "text": "✓ 3 consumers read 3 partitions in parallel = 3× throughput",
          "fontSize": 13,
          "fontFamily": 1,
          "textAlign": "left"
        }
      ],
      "appState": {
        "viewBackgroundColor": "#ffffff"
      }
    }
}%%
