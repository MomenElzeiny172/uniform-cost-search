#include <bits/stdc++.h>
using namespace std;

vector<vector<int> > graph;
/// map to store cost of edges
map<pair<int, int>, int> cost;

vector<int> UCS(vector<int> target, int initial_state) {
	vector<int> answer;
	priority_queue<pair<int, int> > queue;

	for (int i = 0; i < target.size(); i++)
		answer.push_back(INT_MAX);

	queue.push(make_pair(0, initial_state));

	/// map to store visited nodes 'Cities'
	map<int, int> visited;

	int count = 0;

	/// while the queue is not empty
	while (queue.size() > 0) {

		/// get the top element of the priority queue
		pair<int, int> p = queue.top();

		/// pop the element out of the queue
		queue.pop();

		/// get the original value
		p.first *= -1;

		/// check if the element is part of the target list
		if (find(target.begin(), target.end(), p.second) != target.end()) {

			/// get the position index
			int index = find(target.begin(), target.end(),
							p.second) - target.begin();

			/// if a new target is reached
			if (answer[index] == INT_MAX)
				count++;

			/// if the cost is less, takes the less one.
			if (answer[index] > p.first)
				answer[index] = p.first;

			/// pop the element out of the queue
			queue.pop();

			/// if all targets are reached
			if (count == target.size())
				return answer;
		}

		/// check for the non visited nodes which are adjacent to present node
		if (visited[p.second] == 0)
			for (int i = 0; i < graph[p.second].size(); i++) {

				/// value is multiplied by -1 so that least priority is at the top
				queue.push(make_pair((p.first +
				cost[make_pair(p.second, graph[p.second][i])]) * -1,
				graph[p.second][i]));
			}

		/// mark the current city as visited
		visited[p.second] = 1;
	}

	return answer;
}

int main() {
    /**
    ***** Cities (Nodes) Numbers ************
    0 => Arad        **** Initial State
    1 => Zerind
    2 => Timisoara
    3 => Oradea
    4 => Sibui
    5 => Lugoj
    6 => Mehadia
    7 => Fagaras
    8 => Rimnicu Vilcea
    9 => Drobeta
    10 => Craiova
    11 => Pitesti
    12 => Bucharest  **** Target
    13 => Giurgiu
    14 => Eforie
    15 => Hirsova
    16 => Urziceni
    17 => Vaslui
    18 => Lasi
    19 Neamt
    */
	/// create the graph of 20 city
	graph.resize(20);

	/// Edges between cities
	graph[0].push_back(1);
	graph[0].push_back(2);
	graph[1].push_back(3);
	graph[2].push_back(5);
	graph[5].push_back(6);
	graph[6].push_back(9);
	graph[9].push_back(10);
	graph[10].push_back(11);
	graph[10].push_back(8);
	graph[8].push_back(11);
	graph[0].push_back(4);
	graph[3].push_back(4);
	graph[4].push_back(7);
    graph[4].push_back(8);
    graph[11].push_back(12);
    graph[7].push_back(12);
    graph[12].push_back(13);
    graph[12].push_back(16);
    graph[16].push_back(15);
    graph[15].push_back(14);
    graph[16].push_back(17);
    graph[17].push_back(18);
    graph[18].push_back(19);

	/// The cost between cities
	cost[make_pair(0, 1)] = 75;
	cost[make_pair(0, 2)] = 118;
	cost[make_pair(1, 3)] = 71;
	cost[make_pair(2, 5)] = 111;
	cost[make_pair(5, 6)] = 70;
	cost[make_pair(6, 9)] = 75;
	cost[make_pair(9, 10)] = 120;
	cost[make_pair(10, 11)] = 138;
	cost[make_pair(10, 8)] = 146;
	cost[make_pair(8, 11)] = 97;
	cost[make_pair(0, 4)] = 140;
	cost[make_pair(3, 4)] = 151;
    cost[make_pair(4, 7)] = 99;
    cost[make_pair(4, 8)] = 80;
    cost[make_pair(11, 12)] = 101;
    cost[make_pair(7, 12)] = 211;
    cost[make_pair(12, 13)] = 90;
    cost[make_pair(12, 16)] = 85;
    cost[make_pair(16, 15)] = 98;
    cost[make_pair(15, 14)] = 86;
    cost[make_pair(16, 17)] = 142;
    cost[make_pair(17, 18)] = 92;
    cost[make_pair(18, 19)] = 87;



	vector<int> target;
	target.push_back(12); /// Target City node number 12 => Bucharest

	vector<int> answer = UCS(target, 0); /// 0 => aims to Arad node number

	cout << "Minimum cost from Arad (Node \'0\') to Bucharest (Node \'12'\) is = " << answer[0] << endl;

	return 0;
}
