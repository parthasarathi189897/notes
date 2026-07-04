---
excalidraw-plugin: parsed
---
%%{
  excalidraw
    {
      "projectName": "Kafka Consumer Groups",
      "elements": [
        {
          "id": "title",
          "type": "text",
          "x": 200,
          "y": 10,
          "width": 400,
          "height": 25,
          "text": "Consumer Groups — Independent Offset Tracking",
          "fontSize": 18,
          "fontFamily": 1,
          "fontStyle": "bold",
          "textAlign": "center"
        },
        {
          "id": "topic_label",
          "type": "text",
          "x": 80,
          "y": 60,
          "width": 250,
          "height": 20,
          "text": "Topic: orders (3 partitions)",
          "fontSize": 14,
          "fontFamily": 1,
          "fontStyle": "bold"
        },
        {
          "id": "p0_box",
          "type": "rectangle",
          "x": 80,
          "y": 100,
          "width": 120,
          "height": 200,
          "strokeColor": "#0066cc",
          "backgroundColor": "#e6f2ff",
          "strokeWidth": 2
        },
        {
          "id": "p0_label",
          "type": "text",
          "x": 90,
          "y": 110,
          "width": 100,
          "height": 15,
          "text": "Partition 0",
          "fontSize": 12,
          "fontFamily": 1,
          "fontStyle": "bold"
        },
        {
          "id": "p0_events",
          "type": "text",
          "x": 90,
          "y": 135,
          "width": 100,
          "height": 150,
          "text": "[o0] user_123\n[o1] user_456\n[o2] user_123\n[o3] user_789\n[o4] user_123\n[o5] user_111",
          "fontSize": 10,
          "fontFamily": 3
        },
        {
          "id": "p1_box",
          "type": "rectangle",
          "x": 250,
          "y": 100,
          "width": 120,
          "height": 200,
          "strokeColor": "#0066cc",
          "backgroundColor": "#e6f2ff",
          "strokeWidth": 2
        },
        {
          "id": "p1_label",
          "type": "text",
          "x": 260,
          "y": 110,
          "width": 100,
          "height": 15,
          "text": "Partition 1",
          "fontSize": 12,
          "fontFamily": 1,
          "fontStyle": "bold"
        },
        {
          "id": "p1_events",
          "type": "text",
          "x": 260,
          "y": 135,
          "width": 100,
          "height": 150,
          "text": "[o0] user_222\n[o1] user_888\n[o2] user_222\n[o3] user_555\n[o4] user_888",
          "fontSize": 10,
          "fontFamily": 3
        },
        {
          "id": "p2_box",
          "type": "rectangle",
          "x": 420,
          "y": 100,
          "width": 120,
          "height": 200,
          "strokeColor": "#0066cc",
          "backgroundColor": "#e6f2ff",
          "strokeWidth": 2
        },
        {
          "id": "p2_label",
          "type": "text",
          "x": 430,
          "y": 110,
          "width": 100,
          "height": 15,
          "text": "Partition 2",
          "fontSize": 12,
          "fontFamily": 1,
          "fontStyle": "bold"
        },
        {
          "id": "p2_events",
          "type": "text",
          "x": 430,
          "y": 135,
          "width": 100,
          "height": 150,
          "text": "[o0] user_333\n[o1] user_777\n[o2] user_333\n[o3] user_666\n[o4] user_777",
          "fontSize": 10,
          "fontFamily": 3
        },
        {
          "id": "group_a_label",
          "type": "text",
          "x": 80,
          "y": 330,
          "width": 200,
          "height": 20,
          "text": "Consumer Group A",
          "fontSize": 13,
          "fontFamily": 1,
          "fontStyle": "bold",
          "textAlign": "left"
        },
        {
          "id": "group_a_ca",
          "type": "rectangle",
          "x": 80,
          "y": 360,
          "width": 110,
          "height": 70,
          "strokeColor": "#00aa00",
          "backgroundColor": "#e6ffe6",
          "strokeWidth": 2
        },
        {
          "id": "group_a_ca_label",
          "type": "text",
          "x": 90,
          "y": 370,
          "width": 90,
          "height": 15,
          "text": "Consumer A",
          "fontSize": 11,
          "fontFamily": 1
        },
        {
          "id": "group_a_ca_partition",
          "type": "text",
          "x": 90,
          "y": 390,
          "width": 90,
          "height": 15,
          "text": "reads P0",
          "fontSize": 10,
          "fontFamily": 3
        },
        {
          "id": "group_a_ca_offset",
          "type": "text",
          "x": 90,
          "y": 410,
          "width": 90,
          "height": 15,
          "text": "offset at: 3",
          "fontSize": 10,
          "fontFamily": 3,
          "fontStyle": "bold"
        },
        {
          "id": "group_a_cb",
          "type": "rectangle",
          "x": 210,
          "y": 360,
          "width": 110,
          "height": 70,
          "strokeColor": "#00aa00",
          "backgroundColor": "#e6ffe6",
          "strokeWidth": 2
        },
        {
          "id": "group_a_cb_label",
          "type": "text",
          "x": 220,
          "y": 370,
          "width": 90,
          "height": 15,
          "text": "Consumer B",
          "fontSize": 11,
          "fontFamily": 1
        },
        {
          "id": "group_a_cb_partition",
          "type": "text",
          "x": 220,
          "y": 390,
          "width": 90,
          "height": 15,
          "text": "reads P1",
          "fontSize": 10,
          "fontFamily": 3
        },
        {
          "id": "group_a_cb_offset",
          "type": "text",
          "x": 220,
          "y": 410,
          "width": 90,
          "height": 15,
          "text": "offset at: 2",
          "fontSize": 10,
          "fontFamily": 3,
          "fontStyle": "bold"
        },
        {
          "id": "group_a_cc",
          "type": "rectangle",
          "x": 340,
          "y": 360,
          "width": 110,
          "height": 70,
          "strokeColor": "#00aa00",
          "backgroundColor": "#e6ffe6",
          "strokeWidth": 2
        },
        {
          "id": "group_a_cc_label",
          "type": "text",
          "x": 350,
          "y": 370,
          "width": 90,
          "height": 15,
          "text": "Consumer C",
          "fontSize": 11,
          "fontFamily": 1
        },
        {
          "id": "group_a_cc_partition",
          "type": "text",
          "x": 350,
          "y": 390,
          "width": 90,
          "height": 15,
          "text": "reads P2",
          "fontSize": 10,
          "fontFamily": 3
        },
        {
          "id": "group_a_cc_offset",
          "type": "text",
          "x": 350,
          "y": 410,
          "width": 90,
          "height": 15,
          "text": "offset at: 4",
          "fontSize": 10,
          "fontFamily": 3,
          "fontStyle": "bold"
        },
        {
          "id": "arrow_ca_p0",
          "type": "arrow",
          "x": 135,
          "y": 300,
          "x2": 115,
          "y2": 360,
          "strokeColor": "#333333",
          "strokeWidth": 2,
          "endArrowType": "dot"
        },
        {
          "id": "arrow_cb_p1",
          "type": "arrow",
          "x": 310,
          "y": 300,
          "x2": 265,
          "y2": 360,
          "strokeColor": "#333333",
          "strokeWidth": 2,
          "endArrowType": "dot"
        },
        {
          "id": "arrow_cc_p2",
          "type": "arrow",
          "x": 470,
          "y": 300,
          "x2": 395,
          "y2": 360,
          "strokeColor": "#333333",
          "strokeWidth": 2,
          "endArrowType": "dot"
        },
        {
          "id": "group_b_label",
          "type": "text",
          "x": 80,
          "y": 460,
          "width": 200,
          "height": 20,
          "text": "Consumer Group B (independent)",
          "fontSize": 13,
          "fontFamily": 1,
          "fontStyle": "bold",
          "textAlign": "left"
        },
        {
          "id": "group_b_cx",
          "type": "rectangle",
          "x": 80,
          "y": 490,
          "width": 110,
          "height": 70,
          "strokeColor": "#aa00aa",
          "backgroundColor": "#f0e6f0",
          "strokeWidth": 2
        },
        {
          "id": "group_b_cx_label",
          "type": "text",
          "x": 90,
          "y": 500,
          "width": 90,
          "height": 15,
          "text": "Consumer X",
          "fontSize": 11,
          "fontFamily": 1
        },
        {
          "id": "group_b_cx_partition",
          "type": "text",
          "x": 90,
          "y": 520,
          "width": 90,
          "height": 15,
          "text": "reads all 3",
          "fontSize": 10,
          "fontFamily": 3
        },
        {
          "id": "group_b_cx_offset",
          "type": "text",
          "x": 90,
          "y": 540,
          "width": 90,
          "height": 15,
          "text": "offset: 0,0,1",
          "fontSize": 10,
          "fontFamily": 3,
          "fontStyle": "bold"
        },
        {
          "id": "key_point",
          "type": "rectangle",
          "x": 50,
          "y": 600,
          "width": 550,
          "height": 70,
          "strokeColor": "#aa0000",
          "backgroundColor": "#ffe6e6",
          "strokeWidth": 2
        },
        {
          "id": "key_title",
          "type": "text",
          "x": 60,
          "y": 610,
          "width": 530,
          "height": 15,
          "text": "🔑 Each group tracks offsets independently per partition",
          "fontSize": 12,
          "fontFamily": 1,
          "fontStyle": "bold"
        },
        {
          "id": "key_line1",
          "type": "text",
          "x": 60,
          "y": 630,
          "width": 530,
          "height": 15,
          "text": "Group A reads P0 at offset 3 | Group B reads P0 at offset 0 (same partition, different positions!)",
          "fontSize": 11,
          "fontFamily": 1
        },
        {
          "id": "key_line2",
          "type": "text",
          "x": 60,
          "y": 650,
          "width": 530,
          "height": 15,
          "text": "Multiple groups read same topic in parallel without interfering",
          "fontSize": 11,
          "fontFamily": 1
        }
      ],
      "appState": {
        "viewBackgroundColor": "#ffffff"
      }
    }
}%%
