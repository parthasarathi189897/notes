---
excalidraw-plugin: parsed
---
%%{
  excalidraw
    {
      "projectName": "Kafka Key-based Partition Routing",
      "elements": [
        {
          "id": "title",
          "type": "text",
          "x": 250,
          "y": 10,
          "width": 300,
          "height": 25,
          "text": "Key-Based Partition Routing",
          "fontSize": 18,
          "fontFamily": 1,
          "fontStyle": "bold",
          "textAlign": "center"
        },
        {
          "id": "producer_label",
          "type": "text",
          "x": 50,
          "y": 60,
          "width": 100,
          "height": 20,
          "text": "Producer",
          "fontSize": 14,
          "fontFamily": 1,
          "fontStyle": "bold"
        },
        {
          "id": "event1_producer",
          "type": "rectangle",
          "x": 50,
          "y": 90,
          "width": 150,
          "height": 60,
          "strokeColor": "#ff9900",
          "backgroundColor": "#ffe6cc",
          "strokeWidth": 2
        },
        {
          "id": "event1_key",
          "type": "text",
          "x": 60,
          "y": 100,
          "width": 130,
          "height": 15,
          "text": "key = user_123",
          "fontSize": 11,
          "fontFamily": 3
        },
        {
          "id": "event1_value",
          "type": "text",
          "x": 60,
          "y": 120,
          "width": 130,
          "height": 30,
          "text": "value = order data",
          "fontSize": 11,
          "fontFamily": 3
        },
        {
          "id": "event2_producer",
          "type": "rectangle",
          "x": 50,
          "y": 170,
          "width": 150,
          "height": 60,
          "strokeColor": "#ff9900",
          "backgroundColor": "#ffe6cc",
          "strokeWidth": 2
        },
        {
          "id": "event2_key",
          "type": "text",
          "x": 60,
          "y": 180,
          "width": 130,
          "height": 15,
          "text": "key = user_456",
          "fontSize": 11,
          "fontFamily": 3
        },
        {
          "id": "event2_value",
          "type": "text",
          "x": 60,
          "y": 200,
          "width": 130,
          "height": 30,
          "text": "value = order data",
          "fontSize": 11,
          "fontFamily": 3
        },
        {
          "id": "event3_producer",
          "type": "rectangle",
          "x": 50,
          "y": 250,
          "width": 150,
          "height": 60,
          "strokeColor": "#ff9900",
          "backgroundColor": "#ffe6cc",
          "strokeWidth": 2
        },
        {
          "id": "event3_key",
          "type": "text",
          "x": 60,
          "y": 260,
          "width": 130,
          "height": 15,
          "text": "key = user_123",
          "fontSize": 11,
          "fontFamily": 3
        },
        {
          "id": "event3_value",
          "type": "text",
          "x": 60,
          "y": 280,
          "width": 130,
          "height": 30,
          "text": "value = order data",
          "fontSize": 11,
          "fontFamily": 3
        },
        {
          "id": "hash_label",
          "type": "text",
          "x": 250,
          "y": 100,
          "width": 80,
          "height": 20,
          "text": "Hash(key)",
          "fontSize": 12,
          "fontFamily": 1,
          "fontStyle": "bold",
          "textAlign": "center"
        },
        {
          "id": "hash_label2",
          "type": "text",
          "x": 250,
          "y": 180,
          "width": 80,
          "height": 20,
          "text": "Hash(key)",
          "fontSize": 12,
          "fontFamily": 1,
          "fontStyle": "bold",
          "textAlign": "center"
        },
        {
          "id": "hash_label3",
          "type": "text",
          "x": 250,
          "y": 280,
          "width": 80,
          "height": 20,
          "text": "Hash(key)",
          "fontSize": 12,
          "fontFamily": 1,
          "fontStyle": "bold",
          "textAlign": "center"
        },
        {
          "id": "arrow1",
          "type": "arrow",
          "x": 200,
          "y": 120,
          "x2": 250,
          "y2": 120,
          "strokeColor": "#333333",
          "strokeWidth": 2,
          "endArrowType": "dot"
        },
        {
          "id": "arrow2",
          "type": "arrow",
          "x": 200,
          "y": 200,
          "x2": 250,
          "y2": 200,
          "strokeColor": "#333333",
          "strokeWidth": 2,
          "endArrowType": "dot"
        },
        {
          "id": "arrow3",
          "type": "arrow",
          "x": 200,
          "y": 280,
          "x2": 250,
          "y2": 280,
          "strokeColor": "#333333",
          "strokeWidth": 2,
          "endArrowType": "dot"
        },
        {
          "id": "partition_label",
          "type": "text",
          "x": 420,
          "y": 60,
          "width": 150,
          "height": 20,
          "text": "Topic Partitions",
          "fontSize": 14,
          "fontFamily": 1,
          "fontStyle": "bold"
        },
        {
          "id": "p0_destination",
          "type": "rectangle",
          "x": 400,
          "y": 110,
          "width": 150,
          "height": 80,
          "strokeColor": "#0066cc",
          "backgroundColor": "#e6f2ff",
          "strokeWidth": 2
        },
        {
          "id": "p0_dest_label",
          "type": "text",
          "x": 410,
          "y": 120,
          "width": 130,
          "height": 15,
          "text": "Partition 0",
          "fontSize": 12,
          "fontFamily": 1,
          "fontStyle": "bold"
        },
        {
          "id": "p0_dest_event1",
          "type": "text",
          "x": 410,
          "y": 145,
          "width": 130,
          "height": 15,
          "text": "user_123 → offset 0",
          "fontSize": 11,
          "fontFamily": 3
        },
        {
          "id": "p0_dest_event2",
          "type": "text",
          "x": 410,
          "y": 165,
          "width": 130,
          "height": 15,
          "text": "user_123 → offset 1",
          "fontSize": 11,
          "fontFamily": 3
        },
        {
          "id": "p1_destination",
          "type": "rectangle",
          "x": 400,
          "y": 230,
          "width": 150,
          "height": 60,
          "strokeColor": "#0066cc",
          "backgroundColor": "#e6f2ff",
          "strokeWidth": 2
        },
        {
          "id": "p1_dest_label",
          "type": "text",
          "x": 410,
          "y": 240,
          "width": 130,
          "height": 15,
          "text": "Partition 1",
          "fontSize": 12,
          "fontFamily": 1,
          "fontStyle": "bold"
        },
        {
          "id": "p1_dest_event",
          "type": "text",
          "x": 410,
          "y": 265,
          "width": 130,
          "height": 15,
          "text": "user_456 → offset 0",
          "fontSize": 11,
          "fontFamily": 3
        },
        {
          "id": "arrow_to_p0_1",
          "type": "arrow",
          "x": 330,
          "y": 120,
          "x2": 400,
          "y2": 145,
          "strokeColor": "#666666",
          "strokeWidth": 2,
          "endArrowType": "dot"
        },
        {
          "id": "arrow_to_p0_2",
          "type": "arrow",
          "x": 330,
          "y": 280,
          "x2": 400,
          "y2": 165,
          "strokeColor": "#666666",
          "strokeWidth": 2,
          "endArrowType": "dot"
        },
        {
          "id": "arrow_to_p1",
          "type": "arrow",
          "x": 330,
          "y": 200,
          "x2": 400,
          "y2": 265,
          "strokeColor": "#666666",
          "strokeWidth": 2,
          "endArrowType": "dot"
        },
        {
          "id": "key_invariant",
          "type": "rectangle",
          "x": 50,
          "y": 350,
          "width": 500,
          "height": 80,
          "strokeColor": "#aa0000",
          "backgroundColor": "#ffe6e6",
          "strokeWidth": 2
        },
        {
          "id": "invariant_title",
          "type": "text",
          "x": 60,
          "y": 360,
          "width": 480,
          "height": 20,
          "text": "🔑 Key Invariant: Same key always goes to same partition",
          "fontSize": 12,
          "fontFamily": 1,
          "fontStyle": "bold"
        },
        {
          "id": "invariant_line1",
          "type": "text",
          "x": 60,
          "y": 385,
          "width": 480,
          "height": 15,
          "text": "• user_123 always hashes to Partition 0 (no matter when sent)",
          "fontSize": 11,
          "fontFamily": 1
        },
        {
          "id": "invariant_line2",
          "type": "text",
          "x": 60,
          "y": 405,
          "width": 480,
          "height": 15,
          "text": "• All user_123 events process in order (guaranteed ordering)",
          "fontSize": 11,
          "fontFamily": 1
        }
      ],
      "appState": {
        "viewBackgroundColor": "#ffffff"
      }
    }
}%%
