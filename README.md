BGP Router for CS3700


Milestone
We used the Python skeleton provided as starter code. We began with implementing the handle_packet function which dispatches packets to the proper functions based on their type. We then implemented the three methods, update, forward, and dump. We chose to represent our routing table as a dictionary with the network as the key We stored our updates in an array of dictionaries We didn't realize we had to add the ASN in the milestone and initially had lots of trouble diagnosing our errors. We also made a mistake in our helper function that we used for forward to select a route from our forwarding table. The mistake caused our function to consistently return the incorrect route. We found our issue using the simulator output to see that we were sending data packets back to the neighbor that forwarded them to us as opposed to the neighbor that held the destination.

Test levels 1-6

For test level 2 we began by implementing the functions to compare table entry attributes. These functions were relatively simple since they consisted of comparing attributes we already had stored. We didn't have to manipulate the data much. Just check things like which had the shortest aspath or highest localpref. 

Test level 3 was a bit trickier when we realized that we hadn't implemented the send_error() function but instead formatted and sent an error message entirely in the update() function. Once we fixed that we didn't encounter any other serious problems. 

Test level 4
This one wasn't extremely difficult. We just had to get the type of the source interface and the destination, then compare the types and only add an address to outroutes if it was NOT peer to peer/peer to prov/prov to peer

Test level 5
We had to change our lookup routes function to convert the addresses and netmasks to binary and compare them in that format.

Test level 6 was difficult as described in the assignment. We had particular trouble when trying to manipulate the addresses while converting them to and from binary and their normal decimal format. For aggregation we created three flags and iterated through the table. The flags were booleans for the three conditions for aggregation. The loop had another loop nested inside that was also iterating through the forwarding table. When the two loops were on the same entry the nested one would skip it. This method would check some of the same combinations twice so it's not at all optimal, but it worked. The booleans started as false but would become true if that condition for aggregation was satisfied. After checking all of those there's a conditional for all three flags to be true. If they are, the paths would be coalesced by converting them to binary and changing the one bit to store them as an aggregated route. For disaggregation we chose to actually remove and add addresses from our table as opposed to remaking the entire table whenever disaggregation occurred.

